---
title: ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery SQL 使用 WCF 服務模型中的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62f166af-b657-491b-b20d-1ae7886f27ce
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f886463e2b38b358e5f6a9da8b7e67aabdc9c3ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224646"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-sql-using-wcf-service-model"></a><span data-ttu-id="7033b-102">ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery SQL 使用 WCF 服務模型中的作業</span><span class="sxs-lookup"><span data-stu-id="7033b-102">ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model</span></span>
<span data-ttu-id="7033b-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開一般 SQL Server 作業，例如**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。</span><span class="sxs-lookup"><span data-stu-id="7033b-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes generic SQL Server operations such as **ExecuteNonQuery**, **ExecuteReader**, and **ExecuteScalar**.</span></span> <span data-ttu-id="7033b-104">您可以在 SQL Server 資料庫上執行任何 SQL 陳述式中使用這些作業。</span><span class="sxs-lookup"><span data-stu-id="7033b-104">You can use these operations to execute any SQL statement on a SQL Server database.</span></span> <span data-ttu-id="7033b-105">這些作業根據回應您取得 SQL 陳述式的類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="7033b-105">These operations differ based on the kind of response you get for the SQL statement.</span></span> <span data-ttu-id="7033b-106">如需配接器如何支援這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="7033b-106">For more information about how the adapter supports these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
 <span data-ttu-id="7033b-107">本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="7033b-107">This topic demonstrates how to perform an **ExecuteReader** operation using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the WCF service model.</span></span> <span data-ttu-id="7033b-108">您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**和**ExecuteScalar**作業。</span><span class="sxs-lookup"><span data-stu-id="7033b-108">You can follow the same set of procedures described in this topic to perform **ExecuteNonQuery** and **ExecuteScalar** operations.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="7033b-109">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="7033b-109">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="7033b-110">本主題中的範例使用**ExecuteReader**作業執行 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="7033b-110">The example in this topic uses the **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="7033b-111">這個預存程序會將記錄加入 Employee 資料表，並傳回記錄的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="7033b-111">This stored procedure adds a record to the Employee table and returns the employee ID for the record.</span></span> <span data-ttu-id="7033b-112">ADD_EMP_DETAILS 預存程序會建立執行範例所提供的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7033b-112">The ADD_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="7033b-113">如需有關範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7033b-113">For more information about samples, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="7033b-114">範例中， **Execute_Reader**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="7033b-114">A sample, **Execute_Reader**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="7033b-115">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="7033b-115">The WCF Client Class</span></span>  
 <span data-ttu-id="7033b-116">叫用泛型作業 （ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar） 使用產生 WCF 用戶端的名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]列於下表。</span><span class="sxs-lookup"><span data-stu-id="7033b-116">The name of the WCF client generated for invoking generic operations (ExecuteNonQuery, ExecuteReader, or ExecuteScalar) using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="7033b-117">作業</span><span class="sxs-lookup"><span data-stu-id="7033b-117">Operations</span></span>|<span data-ttu-id="7033b-118">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="7033b-118">WCF Client Name</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="7033b-119">ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="7033b-119">ExecuteNonQuery, ExecuteReader, or ExecuteScalar</span></span>|<span data-ttu-id="7033b-120">GenericTableOpClient</span><span class="sxs-lookup"><span data-stu-id="7033b-120">GenericTableOpClient</span></span>|  
  
### <a name="method-signature-for-invoking-generic-operations"></a><span data-ttu-id="7033b-121">叫用泛型作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="7033b-121">Method Signature for Invoking Generic Operations</span></span>  
 <span data-ttu-id="7033b-122">下表顯示公開的方法來叫用泛型作業簽章。</span><span class="sxs-lookup"><span data-stu-id="7033b-122">The following table shows the signature for the method exposed to invoke the generic operations.</span></span>  
  
|<span data-ttu-id="7033b-123">作業</span><span class="sxs-lookup"><span data-stu-id="7033b-123">Operation</span></span>|<span data-ttu-id="7033b-124">方法簽章</span><span class="sxs-lookup"><span data-stu-id="7033b-124">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="7033b-125">ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="7033b-125">ExecuteNonQuery</span></span>|<span data-ttu-id="7033b-126">int ExecuteNonQuery （查詢字串）</span><span class="sxs-lookup"><span data-stu-id="7033b-126">int ExecuteNonQuery(string Query)</span></span>|  
|<span data-ttu-id="7033b-127">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="7033b-127">ExecuteReader</span></span>|<span data-ttu-id="7033b-128">System.Data.DataSet [] ExecuteReader （查詢字串）</span><span class="sxs-lookup"><span data-stu-id="7033b-128">System.Data.DataSet[] ExecuteReader(string Query)</span></span>|  
|<span data-ttu-id="7033b-129">ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="7033b-129">ExecuteScalar</span></span>|<span data-ttu-id="7033b-130">字串 ExecuteScalar(string Query)</span><span class="sxs-lookup"><span data-stu-id="7033b-130">string ExecuteScalar(string Query)</span></span>|  
  
 <span data-ttu-id="7033b-131">為例，下列程式碼片段顯示的一般操作方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="7033b-131">As an example, the signature for the generic operation methods is shown in the following code snippet.</span></span>  
  
```  
public partial class GenericTableOpClient : System.ServiceModel.ClientBase<GenericTableOp>, GenericTableOp {  
  public int ExecuteNonQuery(string Query);  
  public System.Data.DataSet[] ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 <span data-ttu-id="7033b-132">在此片段中，</span><span class="sxs-lookup"><span data-stu-id="7033b-132">In this snippet,</span></span>  
  
-   <span data-ttu-id="7033b-133">`GenericTableOpClient`是類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="7033b-133">`GenericTableOpClient` is the name of the class.</span></span> <span data-ttu-id="7033b-134">在此範例中，您可以使用這個類別來建立叫用泛型作業 ExecuteReader 用戶端。</span><span class="sxs-lookup"><span data-stu-id="7033b-134">In this example, you use this class to create a client to invoke the generic operation, ExecuteReader.</span></span>  
  
-   <span data-ttu-id="7033b-135">`public System.Data.DataSet[] ExecuteReader(string Query)`是，您可以叫用在此範例中叫用 ADD_EMP_DETAILS 方法預存程序。</span><span class="sxs-lookup"><span data-stu-id="7033b-135">`public System.Data.DataSet[] ExecuteReader(string Query)` is the method that you invoke in this example to invoke the ADD_EMP_DETAILS stored procedure.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a><span data-ttu-id="7033b-136">建立 WCF 用戶端來叫用 ExecuteReader 作業</span><span class="sxs-lookup"><span data-stu-id="7033b-136">Creating a WCF Client to Invoke an ExecuteReader Operation</span></span>  
 <span data-ttu-id="7033b-137">使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="7033b-137">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="7033b-138">本節特別說明如何建立 WCF 用戶端叫用**ExecuteReader**作業執行 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="7033b-138">This section specifically describes how to create a WCF client that invokes an **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="7033b-139">這個預存程序會建立執行每個範例提供的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7033b-139">This stored procedure is created by running the SQL script provided with each sample.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a><span data-ttu-id="7033b-140">若要建立 WCF 用戶端來叫用 ExecuteReader 作業</span><span class="sxs-lookup"><span data-stu-id="7033b-140">To create a WCF client to invoke ExecuteReader operation</span></span>  
  
1.  <span data-ttu-id="7033b-141">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="7033b-141">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="7033b-142">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7033b-142">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="7033b-143">產生 WCF 用戶端類別**ExecuteReader**一般作業。</span><span class="sxs-lookup"><span data-stu-id="7033b-143">Generate the WCF client class for the **ExecuteReader** generic operation.</span></span> <span data-ttu-id="7033b-144">根節點下，您可以使用這項作業是當您連接到 SQL Server 資料庫使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7033b-144">This operation is available under the root node when you connect to the SQL Server database using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="7033b-145">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="7033b-145">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7033b-146">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="7033b-146">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="7033b-147">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="7033b-147">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="7033b-148">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="7033b-148">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
            GenericTableOpClient client = new GenericTableOpClient("SqlAdapterBinding_GenericTableOp");  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="7033b-149">在此程式碼片段， `GenericTableOpClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="7033b-149">In this snippet, `GenericTableOpClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="7033b-150">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7033b-150">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="7033b-151">`SqlAdapterBinding_GenericTableOp`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="7033b-151">`SqlAdapterBinding_GenericTableOp` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7033b-152">在此片段中，您從組態檔使用的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="7033b-152">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="7033b-153">您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="7033b-153">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="7033b-154">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="7033b-154">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="7033b-155">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="7033b-155">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="7033b-156">叫用**ExecuteReader** ADD_EMP_DETAILS 的作業預存程序。</span><span class="sxs-lookup"><span data-stu-id="7033b-156">Invoke the **ExecuteReader** operation for the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="7033b-157">您叫用 ExecuteReader 操作之前，您必須加入`System.Data`您的程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7033b-157">Before you invoke the ExecuteReader operation, you must add the `System.Data` namespace to your code.</span></span>  
  
    ```  
    string query = "EXEC ADD_EMP_DETAILS 'Tom Smith', 'Manager', 500000";  
    DataSet[] dsArray = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the ADD_EMP_DETAILS stored procedure using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataSet dataSet in dsArray)  
    {  
       foreach (DataTable tab in dsArray[0].Tables)  
       {  
           foreach (DataRow row in tab.Rows)  
           {  
              for (int i = 0; i < tab.Columns.Count; i++)  
              {  
                 Console.WriteLine("The ID for the newly added employee is : " + row[i]);  
              }  
           }  
        }  
    }  
    Console.WriteLine("*****************************************************");  
  
    ```  
  
7.  <span data-ttu-id="7033b-158">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="7033b-158">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="7033b-159">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="7033b-159">Build the project and then run it.</span></span> <span data-ttu-id="7033b-160">新插入的員工的員工識別碼會顯示在主控台上。</span><span class="sxs-lookup"><span data-stu-id="7033b-160">The employee ID of the newly inserted employee is displayed on the console.</span></span>