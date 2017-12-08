---
title: "插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae613c0e-4d9a-4c66-99e4-dd0443f1d495
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fc9e3968b760be10b428e39662ec3d09db490cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a><span data-ttu-id="e06f3-102">插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-102">Insert, update, delete, or select operations on interface tables and views using the WCF service model</span></span>
<span data-ttu-id="e06f3-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組介面資料表的基本 Insert、 Select、 Update 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on interface tables.</span></span> <span data-ttu-id="e06f3-104">藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式 WHERE 子句的目標介面資料表上所限定。</span><span class="sxs-lookup"><span data-stu-id="e06f3-104">By using these operations, you can perform simple Insert, Select, Update, and Delete statements qualified by a WHERE clause on a target interface table.</span></span> <span data-ttu-id="e06f3-105">本主題提供有關如何執行這些作業使用 WCF 服務模型的指示。</span><span class="sxs-lookup"><span data-stu-id="e06f3-105">This topic provides instructions on how to perform these operations using the WCF service model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e06f3-106">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]只支援選取的介面檢視上的作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-106">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports only Select operations on interface views.</span></span>  
  
 <span data-ttu-id="e06f3-107">如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-107">For more information about how the adapter supports these operations, see [Operations on Interface Tables and Interface Views](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="e06f3-108">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="e06f3-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="e06f3-109">本主題中的範例執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-109">The example in this topic performs operations on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e06f3-110">執行範例所提供的指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="e06f3-110">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="e06f3-111">如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-111">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="e06f3-112">範例中， **Interface_Table_Ops**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e06f3-112">A sample, **Interface_Table_Ops**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="e06f3-113">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="e06f3-113">The WCF Client Class</span></span>  
 <span data-ttu-id="e06f3-114">WCF 用戶端的基本作業產生的名稱，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會探索下表列出根據資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e06f3-114">The name of the WCF client generated for the basic operations that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="e06f3-115">成品</span><span class="sxs-lookup"><span data-stu-id="e06f3-115">Artifact</span></span>|<span data-ttu-id="e06f3-116">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="e06f3-116">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="e06f3-117">介面資料表</span><span class="sxs-lookup"><span data-stu-id="e06f3-117">Interface tables</span></span>|<span data-ttu-id="e06f3-118">InterfaceTables_ [APP_NAME] _ [SCHEMA]\_[TABLE_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="e06f3-118">InterfaceTables_[APP_NAME]_[SCHEMA]\_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="e06f3-119">介面檢視</span><span class="sxs-lookup"><span data-stu-id="e06f3-119">Interface views</span></span>|<span data-ttu-id="e06f3-120">InterfaceViews_ [APP_NAME] _ [SCHEMA]\_[VIEW_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="e06f3-120">InterfaceViews_[APP_NAME]_[SCHEMA]\_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="e06f3-121">[APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。</span><span class="sxs-lookup"><span data-stu-id="e06f3-121">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
 <span data-ttu-id="e06f3-122">[SCHEMA] = 的成品、 集合例如，應用程式。</span><span class="sxs-lookup"><span data-stu-id="e06f3-122">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  
  
 <span data-ttu-id="e06f3-123">[TABLE_NAME] = 表格的名稱例如，MS_SAMPLE_EMPLOYEE。</span><span class="sxs-lookup"><span data-stu-id="e06f3-123">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  
  
 <span data-ttu-id="e06f3-124">[VIEW_NAME] = 檢視; 的名稱例如，MS_SAMPLE_EMPLOYEE_View。</span><span class="sxs-lookup"><span data-stu-id="e06f3-124">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="e06f3-125">叫用資料表上的作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="e06f3-125">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="e06f3-126">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="e06f3-126">The following table shows the method signatures for the basic operations on an table.</span></span> <span data-ttu-id="e06f3-127">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="e06f3-127">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="e06f3-128">作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-128">Operation</span></span>|<span data-ttu-id="e06f3-129">方法簽章</span><span class="sxs-lookup"><span data-stu-id="e06f3-129">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="e06f3-130">Insert</span><span class="sxs-lookup"><span data-stu-id="e06f3-130">Insert</span></span>|<span data-ttu-id="e06f3-131">字串插入 (InsertRecord [資料錄集);</span><span class="sxs-lookup"><span data-stu-id="e06f3-131">string Insert(InsertRecord[] RECORDSET);</span></span>|  
|<span data-ttu-id="e06f3-132">Select</span><span class="sxs-lookup"><span data-stu-id="e06f3-132">Select</span></span>|<span data-ttu-id="e06f3-133">SelectRecord [] 選取 （字串 COLUMN_NAMES，字串篩選條件）。</span><span class="sxs-lookup"><span data-stu-id="e06f3-133">SelectRecord[] Select(string COLUMN_NAMES, string FILTER);</span></span>|  
|<span data-ttu-id="e06f3-134">Update</span><span class="sxs-lookup"><span data-stu-id="e06f3-134">Update</span></span>|<span data-ttu-id="e06f3-135">字串更新 （UpdateRecord 資料錄集，篩選條件字串）;</span><span class="sxs-lookup"><span data-stu-id="e06f3-135">string Update(UpdateRecord RECORDSET, string FILTER);</span></span>|  
|<span data-ttu-id="e06f3-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="e06f3-136">Delete</span></span>|<span data-ttu-id="e06f3-137">刪除 （字串篩選;） 的字串</span><span class="sxs-lookup"><span data-stu-id="e06f3-137">string Delete(string FILTER);</span></span>|  
  
 <span data-ttu-id="e06f3-138">例如，下列程式碼會示範產生 WCF 用戶端類別的方法簽章用於刪除、 插入、 選取和更新作業的預設應用程式結構描述在 MS_SAMPLE_EMPLOYEE 介面資料表上。</span><span class="sxs-lookup"><span data-stu-id="e06f3-138">As an example, the following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the MS_SAMPLE_EMPLOYEE interface table under the default APPS schema.</span></span>  
  
```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  
  
    public string Insert(InsertRecord[] RECORDSET);  
  
    public string Update(UpdateRecord RECORDSET, string FILTER);  
  
    public string Delete(string FILTER);  
}  
```  
  
 <span data-ttu-id="e06f3-139">在此程式碼片段， **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e06f3-139">In this snippet, **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="e06f3-140">資料表作業的參數</span><span class="sxs-lookup"><span data-stu-id="e06f3-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="e06f3-141">本節提供每個資料表作業所需的參數</span><span class="sxs-lookup"><span data-stu-id="e06f3-141">This section provides the parameters required by each table operation</span></span>  
  
 <span data-ttu-id="e06f3-142">**選取作業**</span><span class="sxs-lookup"><span data-stu-id="e06f3-142">**Select Operation**</span></span>  
  
|<span data-ttu-id="e06f3-143">COLUMN_NAMES</span><span class="sxs-lookup"><span data-stu-id="e06f3-143">COLUMN_NAMES</span></span>|<span data-ttu-id="e06f3-144">FILTER</span><span class="sxs-lookup"><span data-stu-id="e06f3-144">FILTER</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="e06f3-145">目標; 中的資料行名稱以逗號分隔清單例如，"EMP_NO，指定"。</span><span class="sxs-lookup"><span data-stu-id="e06f3-145">A comma-delimited list of column names in the target; for example, "EMP_NO, DESIGNATION".</span></span> <span data-ttu-id="e06f3-146">資料行清單中指定的目標所應傳回結果集中的資料行。</span><span class="sxs-lookup"><span data-stu-id="e06f3-146">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="e06f3-147">未指定資料行清單中的資料行會設定為其傳回的記錄組中的.NET 預設值。</span><span class="sxs-lookup"><span data-stu-id="e06f3-147">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="e06f3-148">Nillable 資料行，這個值是**null**。</span><span class="sxs-lookup"><span data-stu-id="e06f3-148">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="e06f3-149">WHERE 子句會指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。</span><span class="sxs-lookup"><span data-stu-id="e06f3-149">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="e06f3-150">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="e06f3-150">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="e06f3-151">選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="e06f3-151">The return value for a Select operation is a strongly-typed result set that contains the specified columns and rows.</span></span>  
  
 <span data-ttu-id="e06f3-152">**插入作業**</span><span class="sxs-lookup"><span data-stu-id="e06f3-152">**Insert Operation**</span></span>  
  
|<span data-ttu-id="e06f3-153">插入作業類型</span><span class="sxs-lookup"><span data-stu-id="e06f3-153">Insert operation type</span></span>|<span data-ttu-id="e06f3-154">資料錄集</span><span class="sxs-lookup"><span data-stu-id="e06f3-154">RECORDSET</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="e06f3-155">多個記錄</span><span class="sxs-lookup"><span data-stu-id="e06f3-155">Multiple record</span></span>|<span data-ttu-id="e06f3-156">應插入至資料表的 INSERTRECORDS 的集合。</span><span class="sxs-lookup"><span data-stu-id="e06f3-156">A collection of INSERTRECORDS that should be inserted into the table.</span></span>|  
  
 <span data-ttu-id="e06f3-157">插入作業的傳回值會是插入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="e06f3-157">The return value for an Insert operation is the number of rows inserted.</span></span>  
  
 <span data-ttu-id="e06f3-158">**更新作業**</span><span class="sxs-lookup"><span data-stu-id="e06f3-158">**Update Operation**</span></span>  
  
|<span data-ttu-id="e06f3-159">資料錄集</span><span class="sxs-lookup"><span data-stu-id="e06f3-159">RECORDSET</span></span>|<span data-ttu-id="e06f3-160">FILTER</span><span class="sxs-lookup"><span data-stu-id="e06f3-160">FILTER</span></span>|  
|---------------|------------|  
|<span data-ttu-id="e06f3-161">應該在資料表中更新的記錄的集合。</span><span class="sxs-lookup"><span data-stu-id="e06f3-161">A collection of records that should be updated in the table.</span></span>|<span data-ttu-id="e06f3-162">WHERE 子句會指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。</span><span class="sxs-lookup"><span data-stu-id="e06f3-162">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="e06f3-163">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="e06f3-163">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="e06f3-164">更新作業的傳回值是更新的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="e06f3-164">The return value for an Update operation is the number of rows updated.</span></span>  
  
 <span data-ttu-id="e06f3-165">**刪除作業**</span><span class="sxs-lookup"><span data-stu-id="e06f3-165">**Delete Operation**</span></span>  
  
 <span data-ttu-id="e06f3-166">刪除作業會輸入一個 WHERE 子句，指定要刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="e06f3-166">The Delete operation takes as input a WHERE clause that specifies the rows to be deleted.</span></span> <span data-ttu-id="e06f3-167">刪除作業的傳回值是刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="e06f3-167">The return value for a Delete operation is the number of rows deleted.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a><span data-ttu-id="e06f3-168">建立 WCF 用戶端來叫用介面資料表上的作業和介面檢視</span><span class="sxs-lookup"><span data-stu-id="e06f3-168">Creating a WCF Client to Invoke Operations on Interface Tables and Interface Views</span></span>  
 <span data-ttu-id="e06f3-169">Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-169">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="e06f3-170">本章節描述如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 介面資料表上的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-170">This section describes how to create a WCF client to invoke basic Insert, Select, Update, Delete operations on an interface table.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a><span data-ttu-id="e06f3-171">若要建立 WCF 用戶端在資料表上執行作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-171">To create a WCF client to perform operations on tables</span></span>  
  
1.  <span data-ttu-id="e06f3-172">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="e06f3-172">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="e06f3-173">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e06f3-173">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="e06f3-174">產生 WCF 用戶端類別的 Insert、 Select、 Update 和刪除 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-174">Generate the WCF client class for the Insert, Select, Update, and Delete operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e06f3-175">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-175">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e06f3-176">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="e06f3-176">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="e06f3-177">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="e06f3-177">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="e06f3-178">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="e06f3-178">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="e06f3-179">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="e06f3-179">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
    ```  
  
     <span data-ttu-id="e06f3-180">在此程式碼片段， `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e06f3-180">In this snippet, `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="e06f3-181">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e06f3-181">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e06f3-182">在此片段中，您明確指定的繫結與端點位址的應用程式程式碼中。</span><span class="sxs-lookup"><span data-stu-id="e06f3-182">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="e06f3-183">您可以使用這些值從應用程式組態檔 app.config，也是由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e06f3-183">You can use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="e06f3-184">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-184">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="e06f3-185">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="e06f3-185">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="e06f3-186">因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="e06f3-186">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="e06f3-187">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e06f3-187">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="e06f3-188">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="e06f3-188">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="e06f3-189">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="e06f3-189">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="e06f3-190">叫用 MS_SAMPLE_EMPLOYEE 資料表的 Insert 作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-190">Invoke the Insert operation on the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
    ```  
    Console.WriteLine("The application will insert a record in the MS_SAMPLE_EMPLOYEE interface table");  
  
    // The date values cannot contain time zone information. Hence, you must use  
    // DateTimeKind.Unspecified to not include the time zone information.  
    DateTime date = new DateTime(DateTime.Now.Ticks, DateTimeKind.Unspecified);  
  
    string result;  
  
    InsertRecord[] recordSet = new InsertRecord[1];  
  
    EMP_NO__COMPLEX_TYPE emp_no = new EMP_NO__COMPLEX_TYPE();  
    emp_no.Value = "10007";  
  
    NAME__COMPLEX_TYPE name = new NAME__COMPLEX_TYPE();  
    name.Value = "John Smith";  
  
    DESIGNATION__COMPLEX_TYPE desig = new DESIGNATION__COMPLEX_TYPE();  
    desig.Value = "Manager";  
  
    SALARY__COMPLEX_TYPE salary = new SALARY__COMPLEX_TYPE();  
    salary.Value = "500000";  
  
    JOIN_DATE__COMPLEX_TYPE doj = new JOIN_DATE__COMPLEX_TYPE();  
    doj.Value = date;  
  
    recordSet[0] = new InsertRecord();  
    recordSet[0].EMP_NO = emp_no;  
    recordSet[0].NAME = name;  
    recordSet[0].DESIGNATION = desig;  
    recordSet[0].SALARY = salary;  
    recordSet[0].JOIN_DATE = doj;  
  
    try  
    {  
       result = client.Insert(recordSet);   
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    Console.WriteLine("Number of records inserted= " + result);  
    Console.WriteLine("Press any key to continue...");  
    Console.ReadLine();  
  
    ```  
  
     <span data-ttu-id="e06f3-191">您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。</span><span class="sxs-lookup"><span data-stu-id="e06f3-191">You can replace the preceding code snippet to perform Select, Update, or Delete operations as well.</span></span> <span data-ttu-id="e06f3-192">您也可以附加到單一應用程式的所有執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="e06f3-192">You can also append the code snippets to perform all operation in a single application.</span></span> <span data-ttu-id="e06f3-193">如需如何執行這些作業程式碼片段，請參閱[選取作業](#BKMK_Select)，[更新作業](#BKMK_Update)，和[刪除作業](#BKMK_Delete)分別。</span><span class="sxs-lookup"><span data-stu-id="e06f3-193">For code snippets on how to perform these operations, see [Select Operation](#BKMK_Select), [Update Operation](#BKMK_Update), and [Delete Operation](#BKMK_Delete) respectively.</span></span>  
  
10. <span data-ttu-id="e06f3-194">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="e06f3-194">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="e06f3-195">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="e06f3-195">Build the project and then run it.</span></span> <span data-ttu-id="e06f3-196">應用程式 MS_SAMPLE_EMPLOYEE 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="e06f3-196">The application inserts a record in the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
###  <a name="BKMK_Select"></a><span data-ttu-id="e06f3-197">選取作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-197">Select Operation</span></span>  
 <span data-ttu-id="e06f3-198">下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的選取作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-198">The following code shows a Select operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="e06f3-199">選取的作業選取插入至資料表的最後一個記錄。</span><span class="sxs-lookup"><span data-stu-id="e06f3-199">The Select operation selects the last record inserted into the table.</span></span> <span data-ttu-id="e06f3-200">傳回的記錄會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="e06f3-200">The returned record is written to the console.</span></span>  
  
```  
Console.WriteLine("The application will now select the last inserted record");  
SelectRecord[] selectRecords;  
try  
{  
   selectRecords = client.Select("*", "WHERE EMP_NO LIKE 10007");  
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
   Console.WriteLine("Employee ID         : " + selectRecords[i].EMP_NO);  
   Console.WriteLine("Employee Name       : " + selectRecords[i].NAME);  
   Console.WriteLine("Employee Desigation : " + selectRecords[i].DESIGNATION);  
   Console.WriteLine("Employee Salary     : " + selectRecords[i].SALARY);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###  <a name="BKMK_Update"></a><span data-ttu-id="e06f3-201">更新作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-201">Update Operation</span></span>  
 <span data-ttu-id="e06f3-202">下列程式碼會示範 MS_SAMPLE_EMPLOYEE 介面資料表為目標的更新作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-202">The following code shows an Update operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
Console.WriteLine("The application will now update the employee name in the newly inserted record");  
string recordsUpdated;  
UpdateRecord updateRecordSet = new UpdateRecord();  
updateRecordSet.NAME = "Tom Smith";  
updateRecordSet.DESIGNATION = "Accountant";  
  
try  
{  
   recordsUpdated = client.Update(updateRecordSet, "WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("No of records updated: " + recordsUpdated);  
Console.WriteLine("Press any key to continue...");  
Console.ReadLine();  
```  
  
###  <a name="BKMK_Delete"></a><span data-ttu-id="e06f3-203">刪除作業</span><span class="sxs-lookup"><span data-stu-id="e06f3-203">Delete Operation</span></span>  
 <span data-ttu-id="e06f3-204">下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="e06f3-204">The following code shows a Delete operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
Console.WriteLine("The sample will now delete the record that it first inserted");  
string deletedRecords;  
try  
{  
   deletedRecords = client.Delete("WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
Console.WriteLine("No of records deleted: " + deletedRecords);  
Console.WriteLine("Press any key to exit...");  
Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="e06f3-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e06f3-205">See Also</span></span>  
 [<span data-ttu-id="e06f3-206">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="e06f3-206">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)