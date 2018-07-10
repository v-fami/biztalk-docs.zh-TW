---
title: 插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae613c0e-4d9a-4c66-99e4-dd0443f1d495
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ed57328a925496449ddd73f3c363b32f60dc811
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983471"
---
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a><span data-ttu-id="d4a2b-102">插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-102">Insert, update, delete, or select operations on interface tables and views using the WCF service model</span></span>
<span data-ttu-id="d4a2b-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組介面資料表上的基本 Insert、 Select、 Update 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on interface tables.</span></span> <span data-ttu-id="d4a2b-104">藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式 WHERE 子句的目標介面資料表上所限定。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-104">By using these operations, you can perform simple Insert, Select, Update, and Delete statements qualified by a WHERE clause on a target interface table.</span></span> <span data-ttu-id="d4a2b-105">本主題提供有關如何使用 WCF 服務模型執行這些作業的指示。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-105">This topic provides instructions on how to perform these operations using the WCF service model.</span></span>  

> [!NOTE]
>  <span data-ttu-id="d4a2b-106">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援只選取介面檢視上的作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-106">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports only Select operations on interface views.</span></span>  

 <span data-ttu-id="d4a2b-107">如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和介面檢視上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-107">For more information about how the adapter supports these operations, see [Operations on Interface Tables and Interface Views](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span></span>  

## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="d4a2b-108">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="d4a2b-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="d4a2b-109">本主題中的範例會執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-109">The example in this topic performs operations on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="d4a2b-110">執行提供的範例指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-110">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="d4a2b-111">如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-111">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="d4a2b-112">範例中， **Interface_Table_Ops**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-112">A sample, **Interface_Table_Ops**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  

## <a name="the-wcf-client-class"></a><span data-ttu-id="d4a2b-113">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="d4a2b-113">The WCF Client Class</span></span>  
 <span data-ttu-id="d4a2b-114">WCF 用戶端的基本作業產生的名稱，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會探索下表所示，為基礎的資料表或檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-114">The name of the WCF client generated for the basic operations that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers is based on the name of the table or view, as listed in the following table.</span></span>  


|     <span data-ttu-id="d4a2b-115">成品</span><span class="sxs-lookup"><span data-stu-id="d4a2b-115">Artifact</span></span>     |                     <span data-ttu-id="d4a2b-116">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="d4a2b-116">WCF Client Name</span></span>                      |
|------------------|----------------------------------------------------------|
| <span data-ttu-id="d4a2b-117">介面資料表</span><span class="sxs-lookup"><span data-stu-id="d4a2b-117">Interface tables</span></span> | <span data-ttu-id="d4a2b-118">InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client</span><span class="sxs-lookup"><span data-stu-id="d4a2b-118">InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client</span></span> |
| <span data-ttu-id="d4a2b-119">介面檢視</span><span class="sxs-lookup"><span data-stu-id="d4a2b-119">Interface views</span></span>  |  <span data-ttu-id="d4a2b-120">InterfaceViews_[APP_NAME]*[SCHEMA]\\*[VIEW_NAME]Client</span><span class="sxs-lookup"><span data-stu-id="d4a2b-120">InterfaceViews_[APP_NAME]*[SCHEMA]\\*[VIEW_NAME]Client</span></span>  |

 <span data-ttu-id="d4a2b-121">[APP_NAME>] = [Oracle E-business Suite 應用程式的實際名稱例如，尋找說明。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-121">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  

 <span data-ttu-id="d4a2b-122">[SCHEMA] = 的成品、 集合例如，應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-122">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  

 <span data-ttu-id="d4a2b-123">[TABLE_NAME] = 資料表的名稱比方說，MS_SAMPLE_EMPLOYEE。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-123">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  

 <span data-ttu-id="d4a2b-124">[VIEW_NAME] = 檢視; 的名稱比方說，MS_SAMPLE_EMPLOYEE_View。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-124">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  

### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="d4a2b-125">叫用資料表上的作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="d4a2b-125">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="d4a2b-126">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-126">The following table shows the method signatures for the basic operations on an table.</span></span> <span data-ttu-id="d4a2b-127">簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-127">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  

|<span data-ttu-id="d4a2b-128">作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-128">Operation</span></span>|<span data-ttu-id="d4a2b-129">方法簽章</span><span class="sxs-lookup"><span data-stu-id="d4a2b-129">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="d4a2b-130">Insert</span><span class="sxs-lookup"><span data-stu-id="d4a2b-130">Insert</span></span>|<span data-ttu-id="d4a2b-131">string Insert(InsertRecord[] RECORDSET);</span><span class="sxs-lookup"><span data-stu-id="d4a2b-131">string Insert(InsertRecord[] RECORDSET);</span></span>|  
|<span data-ttu-id="d4a2b-132">Select</span><span class="sxs-lookup"><span data-stu-id="d4a2b-132">Select</span></span>|<span data-ttu-id="d4a2b-133">SelectRecord[] Select(string COLUMN_NAMES, string FILTER);</span><span class="sxs-lookup"><span data-stu-id="d4a2b-133">SelectRecord[] Select(string COLUMN_NAMES, string FILTER);</span></span>|  
|<span data-ttu-id="d4a2b-134">Update</span><span class="sxs-lookup"><span data-stu-id="d4a2b-134">Update</span></span>|<span data-ttu-id="d4a2b-135">string Update(UpdateRecord RECORDSET, string FILTER);</span><span class="sxs-lookup"><span data-stu-id="d4a2b-135">string Update(UpdateRecord RECORDSET, string FILTER);</span></span>|  
|<span data-ttu-id="d4a2b-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="d4a2b-136">Delete</span></span>|<span data-ttu-id="d4a2b-137">string Delete(string FILTER);</span><span class="sxs-lookup"><span data-stu-id="d4a2b-137">string Delete(string FILTER);</span></span>|  

 <span data-ttu-id="d4a2b-138">例如，下列程式碼顯示產生的 WCF 用戶端類別的方法簽章用於刪除、 插入、 選取及更新的預設應用程式結構描述在 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-138">As an example, the following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the MS_SAMPLE_EMPLOYEE interface table under the default APPS schema.</span></span>  

```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  

    public string Insert(InsertRecord[] RECORDSET);  

    public string Update(UpdateRecord RECORDSET, string FILTER);  

    public string Delete(string FILTER);  
}  
```  

 <span data-ttu-id="d4a2b-139">在此片段中， **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient**是 WCF 中類別的名稱所產生 OracleEBSBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-139">In this snippet, **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

### <a name="parameters-for-table-operations"></a><span data-ttu-id="d4a2b-140">資料表作業的參數</span><span class="sxs-lookup"><span data-stu-id="d4a2b-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="d4a2b-141">本節提供每個資料表作業所需的參數</span><span class="sxs-lookup"><span data-stu-id="d4a2b-141">This section provides the parameters required by each table operation</span></span>  

 <span data-ttu-id="d4a2b-142">**選取作業**</span><span class="sxs-lookup"><span data-stu-id="d4a2b-142">**Select Operation**</span></span>  

|<span data-ttu-id="d4a2b-143">COLUMN_NAMES</span><span class="sxs-lookup"><span data-stu-id="d4a2b-143">COLUMN_NAMES</span></span>|<span data-ttu-id="d4a2b-144">FILTER</span><span class="sxs-lookup"><span data-stu-id="d4a2b-144">FILTER</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="d4a2b-145">目標; 中的資料行名稱的逗號分隔清單例如，"EMP_NO，指定"。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-145">A comma-delimited list of column names in the target; for example, "EMP_NO, DESIGNATION".</span></span> <span data-ttu-id="d4a2b-146">資料行清單中指定目標應該在結果集中傳回之資料的行。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-146">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="d4a2b-147">未指定資料行清單中的資料行，將設為.NET 預設值在傳回的記錄集內。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-147">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="d4a2b-148">Nillable 的資料行，這個值是**null**。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-148">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="d4a2b-149">WHERE 子句，指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-149">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="d4a2b-150">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-150">You can set this parameter to **null** to return all rows of the target.</span></span>|  

 <span data-ttu-id="d4a2b-151">選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-151">The return value for a Select operation is a strongly-typed result set that contains the specified columns and rows.</span></span>  

 <span data-ttu-id="d4a2b-152">**插入作業**</span><span class="sxs-lookup"><span data-stu-id="d4a2b-152">**Insert Operation**</span></span>  

|<span data-ttu-id="d4a2b-153">插入作業類型</span><span class="sxs-lookup"><span data-stu-id="d4a2b-153">Insert operation type</span></span>|<span data-ttu-id="d4a2b-154">資料錄集</span><span class="sxs-lookup"><span data-stu-id="d4a2b-154">RECORDSET</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="d4a2b-155">多個記錄</span><span class="sxs-lookup"><span data-stu-id="d4a2b-155">Multiple record</span></span>|<span data-ttu-id="d4a2b-156">應該插入至資料表的 INSERTRECORDS 的集合。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-156">A collection of INSERTRECORDS that should be inserted into the table.</span></span>|  

 <span data-ttu-id="d4a2b-157">插入作業的傳回值會是插入資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-157">The return value for an Insert operation is the number of rows inserted.</span></span>  

 <span data-ttu-id="d4a2b-158">**更新作業**</span><span class="sxs-lookup"><span data-stu-id="d4a2b-158">**Update Operation**</span></span>  

|<span data-ttu-id="d4a2b-159">資料錄集</span><span class="sxs-lookup"><span data-stu-id="d4a2b-159">RECORDSET</span></span>|<span data-ttu-id="d4a2b-160">FILTER</span><span class="sxs-lookup"><span data-stu-id="d4a2b-160">FILTER</span></span>|  
|---------------|------------|  
|<span data-ttu-id="d4a2b-161">應該在資料表中更新的記錄的集合。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-161">A collection of records that should be updated in the table.</span></span>|<span data-ttu-id="d4a2b-162">WHERE 子句，指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-162">The contents of a WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="d4a2b-163">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-163">You can set this parameter to **null** to return all rows of the target.</span></span>|  

 <span data-ttu-id="d4a2b-164">更新作業的傳回值已更新的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-164">The return value for an Update operation is the number of rows updated.</span></span>  

 <span data-ttu-id="d4a2b-165">**刪除作業**</span><span class="sxs-lookup"><span data-stu-id="d4a2b-165">**Delete Operation**</span></span>  

 <span data-ttu-id="d4a2b-166">刪除作業會採用做為輸入 WHERE 子句，指定要刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-166">The Delete operation takes as input a WHERE clause that specifies the rows to be deleted.</span></span> <span data-ttu-id="d4a2b-167">刪除作業的傳回值是已刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-167">The return value for a Delete operation is the number of rows deleted.</span></span>  

## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a><span data-ttu-id="d4a2b-168">建立 WCF 用戶端來叫用在介面資料表上的作業和介面檢視</span><span class="sxs-lookup"><span data-stu-id="d4a2b-168">Creating a WCF Client to Invoke Operations on Interface Tables and Interface Views</span></span>  
 <span data-ttu-id="d4a2b-169">一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-169">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="d4a2b-170">本節說明如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 介面資料表上的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-170">This section describes how to create a WCF client to invoke basic Insert, Select, Update, Delete operations on an interface table.</span></span>  

#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a><span data-ttu-id="d4a2b-171">若要建立的 WCF 用戶端，在資料表上執行作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-171">To create a WCF client to perform operations on tables</span></span>  

1. <span data-ttu-id="d4a2b-172">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-172">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="d4a2b-173">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-173">For this topic, create a console application.</span></span>  

2. <span data-ttu-id="d4a2b-174">為 Insert、 Select、 Update、 產生 WCF 用戶端類別，並刪除 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-174">Generate the WCF client class for the Insert, Select, Update, and Delete operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="d4a2b-175">如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-175">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="d4a2b-176">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-176">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  

3. <span data-ttu-id="d4a2b-177">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-177">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  

4. <span data-ttu-id="d4a2b-178">開啟 Program.cs 檔案並新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="d4a2b-178">Open the Program.cs file and add the following namespaces:</span></span>  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

5. <span data-ttu-id="d4a2b-179">開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-179">Open the Program.cs file and create a client as described in the snippet below.</span></span>  

   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
   InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
   ```  

    <span data-ttu-id="d4a2b-180">在此片段中， `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-180">In this snippet, `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="d4a2b-181">此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-181">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="d4a2b-182">在此片段中，您明確指定的繫結與端點位址在您的應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-182">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="d4a2b-183">您可以使用這些值，從應用程式組態檔 app.config，也產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-183">You can use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="d4a2b-184">如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-184">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  

6. <span data-ttu-id="d4a2b-185">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-185">Set the credentials for the client.</span></span>  

   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  

7. <span data-ttu-id="d4a2b-186">因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-186">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="d4a2b-187">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，並**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-187">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="d4a2b-188">如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-188">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  

   ```  
   binding.OracleUserName = "myOracleEBSUserName";  
   binding.OraclePassword = "myOracleEBSPassword";  
   binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
   ```  

8. <span data-ttu-id="d4a2b-189">下列程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="d4a2b-189">Open the client as described in the snippet below:</span></span>  

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

9. <span data-ttu-id="d4a2b-190">叫用 MS_SAMPLE_EMPLOYEE 資料表的 Insert 作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-190">Invoke the Insert operation on the MS_SAMPLE_EMPLOYEE table.</span></span>  

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

     <span data-ttu-id="d4a2b-191">您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-191">You can replace the preceding code snippet to perform Select, Update, or Delete operations as well.</span></span> <span data-ttu-id="d4a2b-192">您也可以附加到在單一應用程式中執行所有作業的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-192">You can also append the code snippets to perform all operation in a single application.</span></span> <span data-ttu-id="d4a2b-193">如需如何執行這些作業的程式碼片段，請參閱 <<c0> [ 選取作業](#BKMK_Select)，[更新作業](#BKMK_Update)，並[Delete 作業](#BKMK_Delete)分別。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-193">For code snippets on how to perform these operations, see [Select Operation](#BKMK_Select), [Update Operation](#BKMK_Update), and [Delete Operation](#BKMK_Delete) respectively.</span></span>  

10. <span data-ttu-id="d4a2b-194">下列程式碼片段中所述，請關閉該用戶端：</span><span class="sxs-lookup"><span data-stu-id="d4a2b-194">Close the client as described in the snippet below:</span></span>  

    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  

11. <span data-ttu-id="d4a2b-195">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-195">Build the project and then run it.</span></span> <span data-ttu-id="d4a2b-196">應用程式將 MS_SAMPLE_EMPLOYEE 資料表中插入一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-196">The application inserts a record in the MS_SAMPLE_EMPLOYEE table.</span></span>  

###  <a name="BKMK_Select"></a> <span data-ttu-id="d4a2b-197">選取作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-197">Select Operation</span></span>  
 <span data-ttu-id="d4a2b-198">下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的選取作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-198">The following code shows a Select operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="d4a2b-199">選取的作業選取插入至資料表的最後一個記錄。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-199">The Select operation selects the last record inserted into the table.</span></span> <span data-ttu-id="d4a2b-200">傳回的記錄會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-200">The returned record is written to the console.</span></span>  

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

###  <a name="BKMK_Update"></a> <span data-ttu-id="d4a2b-201">更新作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-201">Update Operation</span></span>  
 <span data-ttu-id="d4a2b-202">下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的更新作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-202">The following code shows an Update operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  

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

###  <a name="BKMK_Delete"></a> <span data-ttu-id="d4a2b-203">刪除作業</span><span class="sxs-lookup"><span data-stu-id="d4a2b-203">Delete Operation</span></span>  
 <span data-ttu-id="d4a2b-204">下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="d4a2b-204">The following code shows a Delete operation that targets the MS_SAMPLE_EMPLOYEE interface table.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="d4a2b-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4a2b-205">See Also</span></span>  
 [<span data-ttu-id="d4a2b-206">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="d4a2b-206">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)