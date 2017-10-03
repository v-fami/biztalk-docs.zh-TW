---
title: "完成 [Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93ba3191-d234-424a-b2da-dcf384df4985
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b671f8fc124875eb5eadf119188d0ffe4c1a2a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="38fa1-102">完成 [Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業</span><span class="sxs-lookup"><span data-stu-id="38fa1-102">Complete operations on tables with large data types in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="38fa1-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行具有大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform operations on interface tables and views with large data types such as BLOB, CLOB, NCLOB, and BFILE.</span></span>  
  
-   <span data-ttu-id="38fa1-104">類型的資料行 BLOB、 CLOB、 和 NCLOB，配接器可讓用戶端可以讀取，以及更新的資料。</span><span class="sxs-lookup"><span data-stu-id="38fa1-104">For columns of type BLOB, CLOB, and NCLOB, the adapter enables clients to read as well as update data.</span></span> <span data-ttu-id="38fa1-105">配接器會公開 Read_\<*LOBColName*> 和 Update_\<*LOBColName*> 作業來讀取和更新資料，其中\< *LOBColName*> 是大型的資料類型資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="38fa1-105">The adapter exposes Read_\<*LOBColName*> and Update_\<*LOBColName*> operations to read and update data respectively, where \<*LOBColName*> is the name of column with large data type.</span></span> <span data-ttu-id="38fa1-106">如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多的讀取和更新該介面資料表的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-106">If there is more than one column with large data type in a single interface table, the adapter exposes as many read and update operations for that interface table.</span></span>  
  
-   <span data-ttu-id="38fa1-107">型別 BFILE 資料行，配接器用戶端可以只讀取資料。</span><span class="sxs-lookup"><span data-stu-id="38fa1-107">For columns of type BFILE, adapter clients can only read data.</span></span> <span data-ttu-id="38fa1-108">配接器會公開 Read_\<*LOBColName*> BFILE 類型的資料行中讀取資料的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-108">The adapter exposes Read_\<*LOBColName*> operation to read data from columns of BFILE type.</span></span> <span data-ttu-id="38fa1-109">如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取介面資料表的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-109">If there is more than one column with large data type in a single interface table, the adapter exposes as many read operations for the interface table.</span></span>  
  
 <span data-ttu-id="38fa1-110">如需有關這些作業的詳細資訊，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-110">For more information about these operations, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="38fa1-111">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="38fa1-111">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="38fa1-112">本主題中的範例更新客戶資料庫資料表中的 BLOB 資料行 （相片），然後從相同的資料行中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="38fa1-112">The example in this topic updates a BLOB column (PHOTO) in the CUSTOMER database table and then retrieves the data from the same column.</span></span> <span data-ttu-id="38fa1-113">執行範例所提供的指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="38fa1-113">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="38fa1-114">如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-114">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="38fa1-115">範例中， **LargeDataTypes_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="38fa1-115">A sample, **LargeDataTypes_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38fa1-116">本主題列出用於更新和讀取大型資料類型的基底資料庫資料表中的資料行的詳細的工作。</span><span class="sxs-lookup"><span data-stu-id="38fa1-116">This topic lists detailed tasks for updating and reading columns of large data types in a base database table.</span></span> <span data-ttu-id="38fa1-117">您必須執行相同的工作集更新和讀取大型資料類型的介面資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="38fa1-117">You must perform the same set of tasks for updating and reading columns of large data types in an interface table.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="38fa1-118">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="38fa1-118">The WCF Client Class</span></span>  
 <span data-ttu-id="38fa1-119">資料表上的作業，使用大型資料類型所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]如下所列於下表根據資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="38fa1-119">The name of the WCF client generated for the operations on tables with large data types by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is based on the name of the table, as listed in the following table.</span></span>  
  
|<span data-ttu-id="38fa1-120">成品</span><span class="sxs-lookup"><span data-stu-id="38fa1-120">Artifact</span></span>|<span data-ttu-id="38fa1-121">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="38fa1-121">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="38fa1-122">介面資料表</span><span class="sxs-lookup"><span data-stu-id="38fa1-122">Interface tables</span></span>|<span data-ttu-id="38fa1-123">InterfaceTables_ [APP_NAME] _ [SCHEMA]\_[TABLE_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="38fa1-123">InterfaceTables_[APP_NAME]_[SCHEMA]\_[TABLE_NAME]Client</span></span>|  
  
 <span data-ttu-id="38fa1-124">[APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。</span><span class="sxs-lookup"><span data-stu-id="38fa1-124">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
 <span data-ttu-id="38fa1-125">[SCHEMA] = 的成品、 集合例如，應用程式。</span><span class="sxs-lookup"><span data-stu-id="38fa1-125">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  
  
 <span data-ttu-id="38fa1-126">[TABLE_NAME] = 表格的名稱例如，MS_SAMPLE_EMPLOYEE。</span><span class="sxs-lookup"><span data-stu-id="38fa1-126">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  
  
 <span data-ttu-id="38fa1-127">[VIEW_NAME] = 檢視; 的名稱例如，MS_SAMPLE_EMPLOYEE_View。</span><span class="sxs-lookup"><span data-stu-id="38fa1-127">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="38fa1-128">叫用資料表上的作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="38fa1-128">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="38fa1-129">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="38fa1-129">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="38fa1-130">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="38fa1-130">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="38fa1-131">作業</span><span class="sxs-lookup"><span data-stu-id="38fa1-131">Operation</span></span>|<span data-ttu-id="38fa1-132">方法簽章</span><span class="sxs-lookup"><span data-stu-id="38fa1-132">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="38fa1-133">Update_\<*column_name*></span><span class="sxs-lookup"><span data-stu-id="38fa1-133">Update_\<*column_name*></span></span>|<span data-ttu-id="38fa1-134">public void Update_\<*column_name*> （字串篩選條件，byte [] 的資料;）</span><span class="sxs-lookup"><span data-stu-id="38fa1-134">public void Update_\<*column_name*>(string FILTER, byte[] DATA);</span></span>|  
|<span data-ttu-id="38fa1-135">Read_\<*column_name*></span><span class="sxs-lookup"><span data-stu-id="38fa1-135">Read_\<*column_name*></span></span>|<span data-ttu-id="38fa1-136">公用 System.IO.Stream Read_\<*column_name*>(string FILTER);</span><span class="sxs-lookup"><span data-stu-id="38fa1-136">public System.IO.Stream Read_\<*column_name*>(string FILTER);</span></span>|  
  
 <span data-ttu-id="38fa1-137">例如，下列程式碼會示範 Update_PHOTO 和 Read_PHOTO 作業的應用程式的結構描述在客戶資料庫資料表上產生 WCF 用戶端類別的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="38fa1-137">As an example, the following code shows the method signatures for a WCF client class generated for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table under the APPS schema.</span></span>  
  
```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      
  
    public void Update_PHOTO(string FILTER, byte[] DATA);  
  
    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  
  
 <span data-ttu-id="38fa1-138">在此程式碼片段， **Tables_APPS_CUSTOMERClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="38fa1-138">In this snippet, **Tables_APPS_CUSTOMERClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="38fa1-139">Update_PHOTO 和 Read_PHOTO 是以更新和讀取資料表中的大型資料類型的資料行就可以叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="38fa1-139">Update_PHOTO and Read_PHOTO are methods that can be invoked to update and read columns of large data types in a table.</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="38fa1-140">資料表作業的參數</span><span class="sxs-lookup"><span data-stu-id="38fa1-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="38fa1-141">本節提供 Update_ 所需的參數\<*column_name*> 和 Read_\<*column_name*> 作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-141">This section provides the parameters required by the Update_\<*column_name*> and Read_\<*column_name*> operation.</span></span>  
  
|<span data-ttu-id="38fa1-142">作業名稱</span><span class="sxs-lookup"><span data-stu-id="38fa1-142">Operation name</span></span>|<span data-ttu-id="38fa1-143">參數</span><span class="sxs-lookup"><span data-stu-id="38fa1-143">Parameters</span></span>|  
|--------------------|----------------|  
|<span data-ttu-id="38fa1-144">Update_\<*column_name*></span><span class="sxs-lookup"><span data-stu-id="38fa1-144">Update_\<*column_name*></span></span>|<span data-ttu-id="38fa1-145">需要下列參數：</span><span class="sxs-lookup"><span data-stu-id="38fa1-145">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="38fa1-146">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="38fa1-146">-   `string FILTER`.</span></span> <span data-ttu-id="38fa1-147">這個參數必須包含 where 子句，表示具有要更新之資料的記錄。</span><span class="sxs-lookup"><span data-stu-id="38fa1-147">This parameter must contain the where clause that denotes the record for which data has to be updated.</span></span> <span data-ttu-id="38fa1-148">例如， `"WHERE Name='Mindy Martin'"`。</span><span class="sxs-lookup"><span data-stu-id="38fa1-148">For example, `"WHERE Name='Mindy Martin'"`.</span></span><br /><span data-ttu-id="38fa1-149">-   `byte[] DATA`.</span><span class="sxs-lookup"><span data-stu-id="38fa1-149">-   `byte[] DATA`.</span></span> <span data-ttu-id="38fa1-150">包含要更新大型資料類型的資料行中資料的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="38fa1-150">Contains a byte array of data to be update in a column of large data type.</span></span>|  
|<span data-ttu-id="38fa1-151">Read_\<*column_name*></span><span class="sxs-lookup"><span data-stu-id="38fa1-151">Read_\<*column_name*></span></span>|<span data-ttu-id="38fa1-152">需要下列參數：</span><span class="sxs-lookup"><span data-stu-id="38fa1-152">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="38fa1-153">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="38fa1-153">-   `string FILTER`.</span></span> <span data-ttu-id="38fa1-154">這個參數必須包含 where 子句代表從中資料有要讀取的記錄。</span><span class="sxs-lookup"><span data-stu-id="38fa1-154">This parameter must contain the where clause that denotes the record from which the data has to be read.</span></span> <span data-ttu-id="38fa1-155">例如， `"WHERE Name='Mindy Martin'"`。</span><span class="sxs-lookup"><span data-stu-id="38fa1-155">For example, `"WHERE Name='Mindy Martin'"`.</span></span>|  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a><span data-ttu-id="38fa1-156">建立 WCF 用戶端來叫用具有大型資料類型之資料行的資料表上的作業</span><span class="sxs-lookup"><span data-stu-id="38fa1-156">Creating a WCF Client to Invoke Operations on Tables with Columns of Large Data Types</span></span>  
 <span data-ttu-id="38fa1-157">Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-157">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="38fa1-158">本章節描述如何建立 WCF 用戶端來叫用 Update_PHOTO 和 Read_PHOTO 客戶資料庫資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-158">This section describes how to create a WCF client to invoke Update_PHOTO and Read_PHOTO operations on a CUSTOMER database table.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="38fa1-159">若要建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="38fa1-159">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="38fa1-160">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="38fa1-160">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="38fa1-161">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="38fa1-161">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="38fa1-162">產生 Update_PHOTO 和 Read_PHOTO 作業客戶資料庫資料表上的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="38fa1-162">Generate the WCF client class for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table.</span></span> <span data-ttu-id="38fa1-163">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-163">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="38fa1-164">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="38fa1-164">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="38fa1-165">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`， `System.Transactions`。</span><span class="sxs-lookup"><span data-stu-id="38fa1-165">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`, `System.Transactions`.</span></span>  
  
4.  <span data-ttu-id="38fa1-166">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="38fa1-166">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.Transactions`  
  
    -   `System.IO`  
  
5.  <span data-ttu-id="38fa1-167">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="38fa1-167">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  
  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="38fa1-168">在此程式碼片段， `Tables_APPS_CUSTOMERClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="38fa1-168">In this snippet, `Tables_APPS_CUSTOMERClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="38fa1-169">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="38fa1-169">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38fa1-170">在此片段中，您可以使用的繫結和端點位址，從組態檔 app.config。您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="38fa1-170">In this snippet, you use the binding and endpoint address from the configuration file app.config. You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="38fa1-171">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-171">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="38fa1-172">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="38fa1-172">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="38fa1-173">在此範例中，您執行資料庫資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="38fa1-173">In this example, you are performing operations on a database table.</span></span> <span data-ttu-id="38fa1-174">不過，如果您正在執行的介面資料表上的作業，您必須設定應用程式內容指定適當的值**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="38fa1-174">However, if you are performing operations on an interface table, you must set the application context by specifying appropriate values for the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="38fa1-175">開啟用戶端之前，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="38fa1-175">You must specify these binding properties before opening the client.</span></span> <span data-ttu-id="38fa1-176">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="38fa1-176">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
7.  <span data-ttu-id="38fa1-177">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="38fa1-177">Open the client as described in the snippet below:</span></span>  
  
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
  
8.  <span data-ttu-id="38fa1-178">叫用 Update_PHOTO 作業，在 CUSTOMER 資料表上。</span><span class="sxs-lookup"><span data-stu-id="38fa1-178">Invoke the Update_PHOTO operation on the CUSTOMER table.</span></span>  
  
     <span data-ttu-id="38fa1-179">Update_PHOTO 作業需要更新資料的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="38fa1-179">The Update_PHOTO operation requires a byte array for the data to be updated.</span></span> <span data-ttu-id="38fa1-180">在此程式碼片段中，您可以使用 FileStream 類別建立的相片，SamplePhoto.jpg 位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="38fa1-180">In this code snippet, you use the FileStream class to create a byte array for a photo, SamplePhoto.jpg.</span></span> <span data-ttu-id="38fa1-181">讓此應用程式運作，檔案必須複製到專案的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="38fa1-181">For this application to work, the file must be copied to the project’s bin directory.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="38fa1-182">Update_PHOTO 作業必須執行在交易中，所以**UseAmbientTransaction**繫結屬性必須設定為**true**和 Update_PHOTO 作業必須在執行交易範圍。</span><span class="sxs-lookup"><span data-stu-id="38fa1-182">The Update_PHOTO operation must be performed in a transaction, so the **UseAmbientTransaction** binding property must be set to **true** and the Update_PHOTO operation must be performed within a transaction scope.</span></span> <span data-ttu-id="38fa1-183">您可以設定**UseAmbientTransaction**在 app.config 中，或藉由明確設定為在應用程式中繫結屬性`binding.UseAmbientTransaction = true`。</span><span class="sxs-lookup"><span data-stu-id="38fa1-183">You can set the **UseAmbientTransaction** binding property either in the app.config or by explicitly setting it in your application as `binding.UseAmbientTransaction = true`.</span></span> <span data-ttu-id="38fa1-184">請注意，是否您要在程式碼中明確指定的繫結屬性，您必須這樣做之前開啟用戶端。</span><span class="sxs-lookup"><span data-stu-id="38fa1-184">Note that if you are specifying the binding property explicitly in the code, you must do so before opening the client.</span></span>  
  
    ```  
    byte[] photo;  
  
    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
    {  
        try  
        {  
            Console.WriteLine("Reading the photo");  
            int count = 0;  
            photo = new byte[fs.Length];  
            while ((count += fs.Read(photo, count, (int)(((fs.Length - count) > 4096) ? 4096 : fs.Length - count))) \< fs.Length) ;  
        }  
        catch(Exception ex)  
        {  
            Console.WriteLine("Exception: " + ex.Message);  
            throw;  
        }  
    }  
  
    Console.WriteLine("Updating data for the 'PHOTO' column");  
    // Invoking the Update_PHOTO operation inside a transaction scope  
    using (TransactionScope tx = new TransactionScope())  
    {  
        string filter = "WHERE Name='Mindy Martin'";  
        client.Update_PHOTO(filter, photo);  
        tx.Complete();  
    }  
  
    ```  
  
9. <span data-ttu-id="38fa1-185">叫用 Read_PHOTO 作業，在 CUSTOMER 資料表上。</span><span class="sxs-lookup"><span data-stu-id="38fa1-185">Invoke the Read_PHOTO operation on the CUSTOMER table.</span></span>  
  
     <span data-ttu-id="38fa1-186">Read_PHOTO 提供 System.IO.Stream 的形式輸出。</span><span class="sxs-lookup"><span data-stu-id="38fa1-186">The Read_PHOTO gives the output in the form of System.IO.Stream.</span></span> <span data-ttu-id="38fa1-187">配接器用戶端必須實作 FileStream 類別 Read_PHOTO 作業中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="38fa1-187">The adapter client must implement the FileStream class to read the data from Read_PHOTO operation.</span></span> <span data-ttu-id="38fa1-188">Read_PHOTO 作業已完成之後，檔案 PhotoCopy.jpg 是會複製到專案的 bin 目錄下。</span><span class="sxs-lookup"><span data-stu-id="38fa1-188">After the Read_PHOTO operation is complete, a file PhotoCopy.jpg is copied under the project’s bin directory.</span></span>  
  
    ```  
    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
    {  
        Console.WriteLine("Reading photo data");  
        String ReadFilter = "WHERE NAME='Mindy Martin'";  
        Stream photoStream = client.Read_PHOTO(ReadFilter);  
        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  
  
        int count;  
        int length = 0;  
        byte[] buffer = new byte[4096];  
        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
        {  
            fs.Write(buffer, 0, count);  
            length+=count;  
        }  
        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
    }  
  
    Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
    Console.ReadLine();  
    ```  
  
10. <span data-ttu-id="38fa1-189">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="38fa1-189">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="38fa1-190">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="38fa1-190">Build the project and then run it.</span></span> <span data-ttu-id="38fa1-191">應用程式更新客戶資料表的 PHOTO 欄，然後再讀取相片的資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="38fa1-191">The application updates the PHOTO column of the CUSTOMER table and then reads the content of the PHOTO column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fa1-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38fa1-192">See Also</span></span>  
 [<span data-ttu-id="38fa1-193">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="38fa1-193">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)