---
title: ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 WCF 服務模型的 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 54c42db1-9a4d-4003-af69-f75ff48b575a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0286de636c2ad9fb50fabafe73b5257d18cf70b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993175"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="f3815-102">使用 WCF 服務模型的 Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業</span><span class="sxs-lookup"><span data-stu-id="f3815-102">ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="f3815-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開一般作業時，這類**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。</span><span class="sxs-lookup"><span data-stu-id="f3815-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes generic operations such as **ExecuteNonQuery**, **ExecuteReader**, and **ExecuteScalar**.</span></span> <span data-ttu-id="f3815-104">Oracle E-business Suite 上執行任何陳述式，您可以使用這些作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-104">You can use these operations to execute any statement on Oracle E-Business Suite.</span></span> <span data-ttu-id="f3815-105">這些作業根據回應您取得陳述式的類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f3815-105">These operations differ based on the kind of response you get for the statement.</span></span> <span data-ttu-id="f3815-106">如需配接器如何支援這些作業的詳細資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-106">For more information about how the adapter supports these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
 <span data-ttu-id="f3815-107">本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="f3815-107">This topic demonstrates how to perform an **ExecuteReader** operation using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] using the WCF service model.</span></span> <span data-ttu-id="f3815-108">您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**並**ExecuteScalar**作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-108">You can follow the same set of procedures described in this topic to perform **ExecuteNonQuery** and **ExecuteScalar** operations.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f3815-109">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="f3815-109">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f3815-110">本主題中的範例會執行**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 介面資料表上的選取作業的作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-110">The example in this topic performs an **ExecuteReader** operation to perform a SELECT operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f3815-111">執行提供的範例指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="f3815-111">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="f3815-112">如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-112">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="f3815-113">範例中， **ExecuteReader**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="f3815-113">A sample, **ExecuteReader**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="f3815-114">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="f3815-114">The WCF Client Class</span></span>  
 <span data-ttu-id="f3815-115">叫用泛型作業 （ExecuteNonQuery、 ExecuteReader、 ExecuteScalar） 使用或產生 WCF 用戶端的名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會列在下表。</span><span class="sxs-lookup"><span data-stu-id="f3815-115">The name of the WCF client generated for invoking generic operations (ExecuteNonQuery, ExecuteReader, or ExecuteScalar) using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="f3815-116">作業</span><span class="sxs-lookup"><span data-stu-id="f3815-116">Operations</span></span>|<span data-ttu-id="f3815-117">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="f3815-117">WCF Client Name</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="f3815-118">ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="f3815-118">ExecuteNonQuery, ExecuteReader, or ExecuteScalar</span></span>|<span data-ttu-id="f3815-119">GenericOperation_Client</span><span class="sxs-lookup"><span data-stu-id="f3815-119">GenericOperation_Client</span></span>|  
  
### <a name="method-signature-for-invoking-generic-operations"></a><span data-ttu-id="f3815-120">叫用泛型作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="f3815-120">Method Signature for Invoking Generic Operations</span></span>  
 <span data-ttu-id="f3815-121">下表來叫用泛型作業所公開的方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="f3815-121">The following table shows the signature for the method exposed to invoke the generic operations.</span></span>  
  
|<span data-ttu-id="f3815-122">作業</span><span class="sxs-lookup"><span data-stu-id="f3815-122">Operation</span></span>|<span data-ttu-id="f3815-123">方法簽章</span><span class="sxs-lookup"><span data-stu-id="f3815-123">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="f3815-124">ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="f3815-124">ExecuteNonQuery</span></span>|<span data-ttu-id="f3815-125">int ExecuteNonQuery （字串查詢，string [] OutputRefCursorNames，System.Data.DataSet [] OutputRefCursors out）</span><span class="sxs-lookup"><span data-stu-id="f3815-125">int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors)</span></span>|  
|<span data-ttu-id="f3815-126">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="f3815-126">ExecuteReader</span></span>|<span data-ttu-id="f3815-127">System.Data.DataSet ExecuteReader(string Query)</span><span class="sxs-lookup"><span data-stu-id="f3815-127">System.Data.DataSet ExecuteReader(string Query)</span></span>|  
|<span data-ttu-id="f3815-128">ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="f3815-128">ExecuteScalar</span></span>|<span data-ttu-id="f3815-129">字串 ExecuteScalar(string Query)</span><span class="sxs-lookup"><span data-stu-id="f3815-129">string ExecuteScalar(string Query)</span></span>|  
  
 <span data-ttu-id="f3815-130">例如，泛型作業方法的簽章會顯示下列程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="f3815-130">As an example, the signature for the generic operation methods is shown in the following code snippet.</span></span>  
  
```  
public partial class GenericOperation_Client : System.ServiceModel.ClientBase<GenericOperation_>, GenericOperation_ {  
  public int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors);  
  public System.Data.DataSet ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 <span data-ttu-id="f3815-131">在此片段中，</span><span class="sxs-lookup"><span data-stu-id="f3815-131">In this snippet,</span></span>  
  
-   <span data-ttu-id="f3815-132">`GenericOperation_Client` 是類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3815-132">`GenericOperation_Client` is the name of the class.</span></span> <span data-ttu-id="f3815-133">這個類別用來建立用戶端來叫用泛型作業，也就是 ExecuteReader。</span><span class="sxs-lookup"><span data-stu-id="f3815-133">This class is used to create a client to invoke the generic operation, ExecuteReader.</span></span>  
  
-   <span data-ttu-id="f3815-134">`public System.Data.DataSet ExecuteReader(string Query)` 是您 MS_SAMPLE_EMPLOYEE 介面資料表上執行 SELECT 陳述式來叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="f3815-134">`public System.Data.DataSet ExecuteReader(string Query)` is the method that you invoke to perform a SELECT statement on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a><span data-ttu-id="f3815-135">建立 WCF 用戶端來叫用 ExecuteReader 操作</span><span class="sxs-lookup"><span data-stu-id="f3815-135">Creating a WCF Client to Invoke an ExecuteReader Operation</span></span>  
 <span data-ttu-id="f3815-136">一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-136">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="f3815-137">本節說明如何建立 WCF 用戶端來叫用**ExecuteReader**作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-137">This section describes how to create a WCF client to invoke the **ExecuteReader** operation.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a><span data-ttu-id="f3815-138">若要建立 WCF 用戶端叫用 ExecuteReader 操作</span><span class="sxs-lookup"><span data-stu-id="f3815-138">To create a WCF client to invoke ExecuteReader operation</span></span>  
  
1. <span data-ttu-id="f3815-139">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="f3815-139">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="f3815-140">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3815-140">For this topic, create a console application.</span></span>  
  
2. <span data-ttu-id="f3815-141">產生 WCF 用戶端類別，如**ExecuteReader**一般作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-141">Generate the WCF client class for the **ExecuteReader** generic operation.</span></span> <span data-ttu-id="f3815-142">這項作業是可用的根節點下，當您連接到 Oracle E-business Suite 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3815-142">This operation is available under the root node when you connect to the Oracle E-Business Suite using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="f3815-143">如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-143">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="f3815-144">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="f3815-144">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3. <span data-ttu-id="f3815-145">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="f3815-145">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4. <span data-ttu-id="f3815-146">開啟 Program.cs 檔案並新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="f3815-146">Open the Program.cs file and add the following namespaces:</span></span>  
  
   -   `Microsoft.Adapters.OracleEBS`  
  
   -   `System.ServiceModel`  
  
5. <span data-ttu-id="f3815-147">在 Program.cs 檔案中，建立用戶端，如下列程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="f3815-147">In the Program.cs file, create a client as described in the snippet below.</span></span>  
  
   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   EndpointAddress address = new EndpointAddress("oracleebs://ebs-72-11");  
   GenericOperation_Client client = new GenericOperation_Client(binding, address);  
   ```  
  
    <span data-ttu-id="f3815-148">在此片段中， `GenericOperation_Client` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="f3815-148">In this snippet, `GenericOperation_Client` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="f3815-149">此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3815-149">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="f3815-150">在此片段中，您明確指定的繫結與端點位址在您的應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3815-150">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="f3815-151">您可以使用這些值，從應用程式組態檔 app.config，也產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3815-151">You can use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="f3815-152">如需指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-152">For more information about the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6. <span data-ttu-id="f3815-153">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="f3815-153">Set the credentials for the client.</span></span>  
  
   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
7. <span data-ttu-id="f3815-154">因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="f3815-154">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="f3815-155">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，並**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f3815-155">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="f3815-156">如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="f3815-156">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
   ```  
   binding.OracleUserName = "myOracleEBSUserName";  
   binding.OraclePassword = "myOracleEBSPassword";  
   binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
   ```  
  
8. <span data-ttu-id="f3815-157">下列程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="f3815-157">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="f3815-158">叫用**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 資料表上的選取作業的作業。</span><span class="sxs-lookup"><span data-stu-id="f3815-158">Invoke the **ExecuteReader** operation for performing the SELECT operation on MS_SAMPLE_EMPLOYEE table.</span></span> <span data-ttu-id="f3815-159">您可以叫用 ExecuteReader 操作之前，您必須新增`System.Data`您的程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f3815-159">Before you invoke the ExecuteReader operation, you must add the `System.Data` namespace to your code.</span></span>  
  
    ```  
    string query = "SELECT * FROM MS_SAMPLE_EMPLOYEE";  
    DataSet ds = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the SELECT statement using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataTable tab in ds.Tables)  
    {  
       foreach (DataRow row in tab.Rows)  
       {  
          Console.WriteLine("The details of the employee are: ");  
          for (int i = 0; i < tab.Columns.Count; i++)  
          {  
             Console.WriteLine(row[i]);  
          }  
          Console.WriteLine();  
       }  
    }  
    Console.WriteLine("*****************************************************");  
    Console.ReadLine();  
  
    ```  
  
10. <span data-ttu-id="f3815-160">下列程式碼片段中所述，請關閉該用戶端：</span><span class="sxs-lookup"><span data-stu-id="f3815-160">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="f3815-161">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="f3815-161">Build the project and then run it.</span></span> <span data-ttu-id="f3815-162">MS_SAMPLE_EMPLOYEE 資料表中的所有記錄會都顯示在主控台上。</span><span class="sxs-lookup"><span data-stu-id="f3815-162">All the records in the MS_SAMPLE_EMPLOYEE table are displayed on the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3815-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3815-163">See Also</span></span>  
 [<span data-ttu-id="f3815-164">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="f3815-164">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)