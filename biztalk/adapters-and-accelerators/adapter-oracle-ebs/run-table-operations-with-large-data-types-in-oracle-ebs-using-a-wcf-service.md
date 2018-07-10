---
title: 完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93ba3191-d234-424a-b2da-dcf384df4985
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9869cd49ed09d80a866f3dcbb6f4b9429788339b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982559"
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="c3587-102">完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業</span><span class="sxs-lookup"><span data-stu-id="c3587-102">Complete operations on tables with large data types in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="c3587-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端來執行大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to perform operations on interface tables and views with large data types such as BLOB, CLOB, NCLOB, and BFILE.</span></span>  

- <span data-ttu-id="c3587-104">類型的資料行 BLOB、 CLOB、 和 NCLOB，此配接器可以讀取，以及更新資料的用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3587-104">For columns of type BLOB, CLOB, and NCLOB, the adapter enables clients to read as well as update data.</span></span> <span data-ttu-id="c3587-105">配接器會公開 Read_\<*LOBColName* \>和 Update_\<*LOBColName* \>作業來讀取和更新資料，其中\<*LOBColName* \>是具有大型的資料類型的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3587-105">The adapter exposes Read_\<*LOBColName*\> and Update_\<*LOBColName*\> operations to read and update data respectively, where \<*LOBColName*\> is the name of column with large data type.</span></span> <span data-ttu-id="c3587-106">如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取和更新該介面資料表的作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-106">If there is more than one column with large data type in a single interface table, the adapter exposes as many read and update operations for that interface table.</span></span>  

- <span data-ttu-id="c3587-107">型別 BFILE 資料行，配接器用戶端只能讀取資料。</span><span class="sxs-lookup"><span data-stu-id="c3587-107">For columns of type BFILE, adapter clients can only read data.</span></span> <span data-ttu-id="c3587-108">配接器會公開 Read_\<*LOBColName* \> BFILE 類型的資料行中讀取資料的作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-108">The adapter exposes Read_\<*LOBColName*\> operation to read data from columns of BFILE type.</span></span> <span data-ttu-id="c3587-109">如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取作業的介面資料表。</span><span class="sxs-lookup"><span data-stu-id="c3587-109">If there is more than one column with large data type in a single interface table, the adapter exposes as many read operations for the interface table.</span></span>  

  <span data-ttu-id="c3587-110">如需有關這些作業的詳細資訊，請參閱 < [Interface Table、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-110">For more information about these operations, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span></span>  

## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="c3587-111">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="c3587-111">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="c3587-112">本主題中的範例會更新客戶資料庫資料表中的 BLOB 資料行 （相片），並接著會從相同的資料行的擷取資料。</span><span class="sxs-lookup"><span data-stu-id="c3587-112">The example in this topic updates a BLOB column (PHOTO) in the CUSTOMER database table and then retrieves the data from the same column.</span></span> <span data-ttu-id="c3587-113">執行提供的範例指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="c3587-113">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="c3587-114">如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-114">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="c3587-115">範例中， **LargeDataTypes_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="c3587-115">A sample, **LargeDataTypes_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  

> [!NOTE]
>  <span data-ttu-id="c3587-116">本主題列出用於更新和讀取大型資料類型的基底資料庫資料表中的資料行的詳細的工作。</span><span class="sxs-lookup"><span data-stu-id="c3587-116">This topic lists detailed tasks for updating and reading columns of large data types in a base database table.</span></span> <span data-ttu-id="c3587-117">您必須執行同一組工作來更新和讀取在介面資料表中的大型資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="c3587-117">You must perform the same set of tasks for updating and reading columns of large data types in an interface table.</span></span>  

## <a name="the-wcf-client-class"></a><span data-ttu-id="c3587-118">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="c3587-118">The WCF Client Class</span></span>  
 <span data-ttu-id="c3587-119">WCF 用戶端中的資料表上作業，使用大型資料類型所產生的名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]下表所示，根據資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3587-119">The name of the WCF client generated for the operations on tables with large data types by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is based on the name of the table, as listed in the following table.</span></span>  


|     <span data-ttu-id="c3587-120">成品</span><span class="sxs-lookup"><span data-stu-id="c3587-120">Artifact</span></span>     |                     <span data-ttu-id="c3587-121">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="c3587-121">WCF Client Name</span></span>                      |
|------------------|----------------------------------------------------------|
| <span data-ttu-id="c3587-122">介面資料表</span><span class="sxs-lookup"><span data-stu-id="c3587-122">Interface tables</span></span> | <span data-ttu-id="c3587-123">InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client</span><span class="sxs-lookup"><span data-stu-id="c3587-123">InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client</span></span> |

 <span data-ttu-id="c3587-124">[APP_NAME>] = [Oracle E-business Suite 應用程式的實際名稱例如，尋找說明。</span><span class="sxs-lookup"><span data-stu-id="c3587-124">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  

 <span data-ttu-id="c3587-125">[SCHEMA] = 的成品、 集合例如，應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3587-125">[SCHEMA] = Collection of artifacts; for example, APPS.</span></span>  

 <span data-ttu-id="c3587-126">[TABLE_NAME] = 資料表的名稱比方說，MS_SAMPLE_EMPLOYEE。</span><span class="sxs-lookup"><span data-stu-id="c3587-126">[TABLE_NAME] = The name of the table; for example, MS_SAMPLE_EMPLOYEE.</span></span>  

 <span data-ttu-id="c3587-127">[VIEW_NAME] = 檢視; 的名稱比方說，MS_SAMPLE_EMPLOYEE_View。</span><span class="sxs-lookup"><span data-stu-id="c3587-127">[VIEW_NAME] = The name of the view; for example, MS_SAMPLE_EMPLOYEE_View.</span></span>  

### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="c3587-128">叫用資料表上的作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="c3587-128">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="c3587-129">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="c3587-129">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="c3587-130">簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。</span><span class="sxs-lookup"><span data-stu-id="c3587-130">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  

|<span data-ttu-id="c3587-131">作業</span><span class="sxs-lookup"><span data-stu-id="c3587-131">Operation</span></span>|<span data-ttu-id="c3587-132">方法簽章</span><span class="sxs-lookup"><span data-stu-id="c3587-132">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="c3587-133">Update_\<*column_name*\></span><span class="sxs-lookup"><span data-stu-id="c3587-133">Update_\<*column_name*\></span></span>|<span data-ttu-id="c3587-134">public void Update_\<*column_name*\>（字串篩選條件，byte [] 的資料;）</span><span class="sxs-lookup"><span data-stu-id="c3587-134">public void Update_\<*column_name*\>(string FILTER, byte[] DATA);</span></span>|  
|<span data-ttu-id="c3587-135">Read_\<*column_name*\></span><span class="sxs-lookup"><span data-stu-id="c3587-135">Read_\<*column_name*\></span></span>|<span data-ttu-id="c3587-136">public System.IO.Stream Read_\<*column_name*\>(string FILTER);</span><span class="sxs-lookup"><span data-stu-id="c3587-136">public System.IO.Stream Read_\<*column_name*\>(string FILTER);</span></span>|  

 <span data-ttu-id="c3587-137">例如，下列的程式碼會示範針對 Update_PHOTO 和 Read_PHOTO 作業的應用程式結構描述在客戶資料庫資料表上所產生的 WCF 用戶端類別的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="c3587-137">As an example, the following code shows the method signatures for a WCF client class generated for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table under the APPS schema.</span></span>  

```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      

    public void Update_PHOTO(string FILTER, byte[] DATA);  

    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  

 <span data-ttu-id="c3587-138">在此片段中， **Tables_APPS_CUSTOMERClient**是 WCF 中類別的名稱所產生 OracleEBSBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c3587-138">In this snippet, **Tables_APPS_CUSTOMERClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="c3587-139">Update_PHOTO Read_PHOTO 等可以叫用它來更新和讀取資料表中的大型資料類型的資料行的方法。</span><span class="sxs-lookup"><span data-stu-id="c3587-139">Update_PHOTO and Read_PHOTO are methods that can be invoked to update and read columns of large data types in a table.</span></span>  

### <a name="parameters-for-table-operations"></a><span data-ttu-id="c3587-140">資料表作業的參數</span><span class="sxs-lookup"><span data-stu-id="c3587-140">Parameters for Table Operations</span></span>  
 <span data-ttu-id="c3587-141">本節提供 Update_ 所需的參數\<*column_name* \>和 Read_\<*column_name* \>作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-141">This section provides the parameters required by the Update_\<*column_name*\> and Read_\<*column_name*\> operation.</span></span>  

|<span data-ttu-id="c3587-142">作業名稱</span><span class="sxs-lookup"><span data-stu-id="c3587-142">Operation name</span></span>|<span data-ttu-id="c3587-143">參數</span><span class="sxs-lookup"><span data-stu-id="c3587-143">Parameters</span></span>|  
|--------------------|----------------|  
|<span data-ttu-id="c3587-144">Update_\<*column_name*\></span><span class="sxs-lookup"><span data-stu-id="c3587-144">Update_\<*column_name*\></span></span>|<span data-ttu-id="c3587-145">需要下列參數：</span><span class="sxs-lookup"><span data-stu-id="c3587-145">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="c3587-146">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="c3587-146">-   `string FILTER`.</span></span> <span data-ttu-id="c3587-147">這個參數必須包含 where 子句，表示具有更新之資料的記錄。</span><span class="sxs-lookup"><span data-stu-id="c3587-147">This parameter must contain the where clause that denotes the record for which data has to be updated.</span></span> <span data-ttu-id="c3587-148">例如， `"WHERE Name='Mindy Martin'"`。</span><span class="sxs-lookup"><span data-stu-id="c3587-148">For example, `"WHERE Name='Mindy Martin'"`.</span></span><br /><span data-ttu-id="c3587-149">-   `byte[] DATA`.</span><span class="sxs-lookup"><span data-stu-id="c3587-149">-   `byte[] DATA`.</span></span> <span data-ttu-id="c3587-150">包含要更新的大型資料類型資料行中資料的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c3587-150">Contains a byte array of data to be update in a column of large data type.</span></span>|  
|<span data-ttu-id="c3587-151">Read_\<*column_name*\></span><span class="sxs-lookup"><span data-stu-id="c3587-151">Read_\<*column_name*\></span></span>|<span data-ttu-id="c3587-152">需要下列參數：</span><span class="sxs-lookup"><span data-stu-id="c3587-152">Requires the following parameters:</span></span><br /><br /> <span data-ttu-id="c3587-153">-   `string FILTER`.</span><span class="sxs-lookup"><span data-stu-id="c3587-153">-   `string FILTER`.</span></span> <span data-ttu-id="c3587-154">這個參數必須包含 where 子句，表示來源的資料具有讀取的記錄。</span><span class="sxs-lookup"><span data-stu-id="c3587-154">This parameter must contain the where clause that denotes the record from which the data has to be read.</span></span> <span data-ttu-id="c3587-155">例如， `"WHERE Name='Mindy Martin'"`。</span><span class="sxs-lookup"><span data-stu-id="c3587-155">For example, `"WHERE Name='Mindy Martin'"`.</span></span>|  

## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a><span data-ttu-id="c3587-156">建立 WCF 用戶端來叫用具有大型資料類型之資料行的資料表上的作業</span><span class="sxs-lookup"><span data-stu-id="c3587-156">Creating a WCF Client to Invoke Operations on Tables with Columns of Large Data Types</span></span>  
 <span data-ttu-id="c3587-157">一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-157">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="c3587-158">本節說明如何建立 WCF 用戶端來叫用 Update_PHOTO 和 Read_PHOTO 客戶資料庫資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-158">This section describes how to create a WCF client to invoke Update_PHOTO and Read_PHOTO operations on a CUSTOMER database table.</span></span>  

#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="c3587-159">若要建立的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="c3587-159">To create a WCF client</span></span>  

1. <span data-ttu-id="c3587-160">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="c3587-160">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="c3587-161">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3587-161">For this topic, create a console application.</span></span>  

2. <span data-ttu-id="c3587-162">產生 WCF 用戶端類別，針對 Update_PHOTO 和 Read_PHOTO 作業會在客戶資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="c3587-162">Generate the WCF client class for the Update_PHOTO and Read_PHOTO operations on the CUSTOMER database table.</span></span> <span data-ttu-id="c3587-163">如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-163">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="c3587-164">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="c3587-164">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  

3. <span data-ttu-id="c3587-165">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`並`Microsoft.ServiceModel.Channels`， `System.Transactions`。</span><span class="sxs-lookup"><span data-stu-id="c3587-165">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`, `System.Transactions`.</span></span>  

4. <span data-ttu-id="c3587-166">開啟 Program.cs 檔案並新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="c3587-166">Open the Program.cs file and add the following namespaces:</span></span>  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

   -   `System.Transactions`  

   -   `System.IO`  

5. <span data-ttu-id="c3587-167">開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="c3587-167">Open the Program.cs file and create a client as described in the snippet below.</span></span>  

   ```  

             Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  

   client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  

    <span data-ttu-id="c3587-168">在此片段中， `Tables_APPS_CUSTOMERClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3587-168">In this snippet, `Tables_APPS_CUSTOMERClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="c3587-169">此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c3587-169">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="c3587-170">在此片段中，您可以使用的繫結和端點位址，從組態檔 app.config。您也可以明確指定這些值在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c3587-170">In this snippet, you use the binding and endpoint address from the configuration file app.config. You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="c3587-171">如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-171">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  

6. <span data-ttu-id="c3587-172">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="c3587-172">Set the credentials for the client.</span></span>  

   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  

   > [!IMPORTANT]
   >  <span data-ttu-id="c3587-173">在此範例中，您要執行的資料庫資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="c3587-173">In this example, you are performing operations on a database table.</span></span> <span data-ttu-id="c3587-174">不過，如果您要執行在介面資料表上的作業，您必須設定應用程式內容指定適當的值，如**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c3587-174">However, if you are performing operations on an interface table, you must set the application context by specifying appropriate values for the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="c3587-175">開啟用戶端之前，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c3587-175">You must specify these binding properties before opening the client.</span></span> <span data-ttu-id="c3587-176">如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="c3587-176">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  

7. <span data-ttu-id="c3587-177">下列程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="c3587-177">Open the client as described in the snippet below:</span></span>  

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

8. <span data-ttu-id="c3587-178">叫用 Update_PHOTO 作業，在 CUSTOMER 資料表上。</span><span class="sxs-lookup"><span data-stu-id="c3587-178">Invoke the Update_PHOTO operation on the CUSTOMER table.</span></span>  

    <span data-ttu-id="c3587-179">Update_PHOTO 作業需要更新資料的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c3587-179">The Update_PHOTO operation requires a byte array for the data to be updated.</span></span> <span data-ttu-id="c3587-180">在此程式碼片段中，您可以使用 FileStream 類別建立一張照片，SamplePhoto.jpg 的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c3587-180">In this code snippet, you use the FileStream class to create a byte array for a photo, SamplePhoto.jpg.</span></span> <span data-ttu-id="c3587-181">使用此應用程式，該檔案必須複製到專案的 bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="c3587-181">For this application to work, the file must be copied to the project’s bin directory.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="c3587-182">Update_PHOTO 作業只能在交易中，因此**UseAmbientTransaction**繫結屬性必須設定為 **，則為 true**和 Update_PHOTO 作業必須在中執行交易範圍。</span><span class="sxs-lookup"><span data-stu-id="c3587-182">The Update_PHOTO operation must be performed in a transaction, so the **UseAmbientTransaction** binding property must be set to **true** and the Update_PHOTO operation must be performed within a transaction scope.</span></span> <span data-ttu-id="c3587-183">您可以設定**UseAmbientTransaction** app.config 中或藉由明確將您的應用程式中將屬性繫結`binding.UseAmbientTransaction = true`。</span><span class="sxs-lookup"><span data-stu-id="c3587-183">You can set the **UseAmbientTransaction** binding property either in the app.config or by explicitly setting it in your application as `binding.UseAmbientTransaction = true`.</span></span> <span data-ttu-id="c3587-184">請注意，是否您要在程式碼中明確指定的繫結屬性，您必須這麼做之前開啟用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3587-184">Note that if you are specifying the binding property explicitly in the code, you must do so before opening the client.</span></span>  

   ```  
   byte[] photo;  

   using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
   {  
       try  
       {  
           Console.WriteLine("Reading the photo");  
           int count = 0;  
           photo = new byte[fs.Length];  
           while ((count += fs.Read(photo, count, (int)(((fs.Length - count) > 4096) ? 4096 : fs.Length - count))) < fs.Length) ;  
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

9. <span data-ttu-id="c3587-185">叫用 Read_PHOTO 作業，在 CUSTOMER 資料表上。</span><span class="sxs-lookup"><span data-stu-id="c3587-185">Invoke the Read_PHOTO operation on the CUSTOMER table.</span></span>  

     <span data-ttu-id="c3587-186">Read_PHOTO 提供 System.IO.Stream 的形式輸出。</span><span class="sxs-lookup"><span data-stu-id="c3587-186">The Read_PHOTO gives the output in the form of System.IO.Stream.</span></span> <span data-ttu-id="c3587-187">配接器用戶端必須實作 FileStream 類別從 Read_PHOTO 作業讀取資料。</span><span class="sxs-lookup"><span data-stu-id="c3587-187">The adapter client must implement the FileStream class to read the data from Read_PHOTO operation.</span></span> <span data-ttu-id="c3587-188">Read_PHOTO 作業完成之後，檔案 PhotoCopy.jpg 是會複製到專案的 bin 目錄下。</span><span class="sxs-lookup"><span data-stu-id="c3587-188">After the Read_PHOTO operation is complete, a file PhotoCopy.jpg is copied under the project’s bin directory.</span></span>  

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

10. <span data-ttu-id="c3587-189">下列程式碼片段中所述，請關閉該用戶端：</span><span class="sxs-lookup"><span data-stu-id="c3587-189">Close the client as described in the snippet below:</span></span>  

    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  

11. <span data-ttu-id="c3587-190">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="c3587-190">Build the project and then run it.</span></span> <span data-ttu-id="c3587-191">應用程式更新 CUSTOMER 資料表的 PHOTO 資料行，然後再讀取 PHOTO 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="c3587-191">The application updates the PHOTO column of the CUSTOMER table and then reads the content of the PHOTO column.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c3587-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3587-192">See Also</span></span>  
 [<span data-ttu-id="c3587-193">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="c3587-193">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)