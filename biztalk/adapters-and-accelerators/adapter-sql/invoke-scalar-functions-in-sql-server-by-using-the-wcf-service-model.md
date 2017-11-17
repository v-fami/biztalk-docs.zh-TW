---
title: "使用 WCF 服務模型來叫用 SQL Server 中的純量函數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a331e275-3c81-41a8-9ba1-3a801ebc259a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0303378f6e265d3b5d86a1aa9cd4fb1e88df86fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model"></a><span data-ttu-id="0b876-102">使用 WCF 服務模型來叫用 SQL Server 中的純量函式</span><span class="sxs-lookup"><span data-stu-id="0b876-102">Invoke Scalar Functions in SQL Server by Using the WCF Service Model</span></span>
<span data-ttu-id="0b876-103">您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].NET 應用程式使用 WCF 服務模型來叫用 SQL Server 中的純量函式中。</span><span class="sxs-lookup"><span data-stu-id="0b876-103">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET application using the WCF service model to invoke scalar functions in SQL Server.</span></span> <span data-ttu-id="0b876-104">配接器會公開為可直接在 SQL Server 上叫用方法的純量函數。</span><span class="sxs-lookup"><span data-stu-id="0b876-104">The adapter exposes the scalar functions as methods that can be invoked directly on SQL Server.</span></span> <span data-ttu-id="0b876-105">如需配接器如何支援純量函數的詳細資訊，請參閱[執行 SQL Server 使用 SQL 配接器中的純量函式](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-105">For more information about how the adapter supports scalar functions, see [Execute Scalar Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
## <a name="how-this-topic-demonstrates-invoking-scalar-functions-using-the-wcf-service-model"></a><span data-ttu-id="0b876-106">本主題示範叫用純量函數使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="0b876-106">How This Topic Demonstrates Invoking Scalar Functions Using the WCF Service Model</span></span>  
 <span data-ttu-id="0b876-107">本主題示範如何叫用 SQL Server 資料庫中的 GET_EMP_ID 函式。</span><span class="sxs-lookup"><span data-stu-id="0b876-107">This topic demonstrates how to invoke the GET_EMP_ID function in a SQL Server database.</span></span> <span data-ttu-id="0b876-108">GET_EMP_ID 函式中的員工的指定**員工**資料表，並傳回對應的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b876-108">The GET_EMP_ID function takes the designation of an employee in the **Employee** table and returns the corresponding employee ID.</span></span> <span data-ttu-id="0b876-109">GET_EMP_ID 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="0b876-109">The GET_EMP_ID function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="0b876-110">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-110">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="0b876-111">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="0b876-111">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="0b876-112">本主題中的範例叫用之員工資料表的 GET_EMP_ID 純量函數。</span><span class="sxs-lookup"><span data-stu-id="0b876-112">The example in this topic invoked the GET_EMP_ID scalar function on the Employee table.</span></span> <span data-ttu-id="0b876-113">GET_EMP_ID 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="0b876-113">The GET_EMP_ID function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="0b876-114">範例中， **ScalarFunction_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0b876-114">A sample, **ScalarFunction_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span> <span data-ttu-id="0b876-115">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-115">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="0b876-116">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="0b876-116">The WCF Client Class</span></span>  
 <span data-ttu-id="0b876-117">叫用純量函數中使用 SQL Server 產生 WCF 用戶端的名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]列於下表。</span><span class="sxs-lookup"><span data-stu-id="0b876-117">The name of the WCF client generated for invoking the scalar function in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="0b876-118">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="0b876-118">SQL Server Database Artifact</span></span>|<span data-ttu-id="0b876-119">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="0b876-119">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="0b876-120">純量函數</span><span class="sxs-lookup"><span data-stu-id="0b876-120">Scalar function</span></span>|<span data-ttu-id="0b876-121">ScalarFunctions_ [SCHEMA] 用戶端</span><span class="sxs-lookup"><span data-stu-id="0b876-121">ScalarFunctions_[SCHEMA]Client</span></span>|  
  
 <span data-ttu-id="0b876-122">[SCHEMA] = 集合 SQL Server 成品。例如，dbo。</span><span class="sxs-lookup"><span data-stu-id="0b876-122">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-scalar-functions"></a><span data-ttu-id="0b876-123">方法簽章的叫用純量函數</span><span class="sxs-lookup"><span data-stu-id="0b876-123">Method Signature for Invoking Scalar Functions</span></span>  
 <span data-ttu-id="0b876-124">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="0b876-124">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="0b876-125">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="0b876-125">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="0b876-126">作業</span><span class="sxs-lookup"><span data-stu-id="0b876-126">Operation</span></span>|<span data-ttu-id="0b876-127">方法簽章</span><span class="sxs-lookup"><span data-stu-id="0b876-127">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="0b876-128">純量函數名稱</span><span class="sxs-lookup"><span data-stu-id="0b876-128">Scalar function name</span></span>|<span data-ttu-id="0b876-129">公用*< return_type >**< scalar_function_name >*(參數 1，參數 2，...)</span><span class="sxs-lookup"><span data-stu-id="0b876-129">public *<return_type>**<scalar_function_name>*(param1, param2, …)</span></span>|  
  
 <span data-ttu-id="0b876-130">\<*retrun_type*> = 函式定義中所定義的傳回型別</span><span class="sxs-lookup"><span data-stu-id="0b876-130">\<*retrun_type*> = Return type defined in the function definition</span></span>  
  
 <span data-ttu-id="0b876-131">\<*scalar_function_name*> = 純量函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b876-131">\<*scalar_function_name*> = Name of the scalar function.</span></span>  
  
 <span data-ttu-id="0b876-132">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**GET_EMP_ID** dbo 結構描述，它做為參數指定的員工，並傳回員工識別碼 （中的純量函式整數）。</span><span class="sxs-lookup"><span data-stu-id="0b876-132">As an example, the following code shows the method signatures for a WCF client class generated for the **GET_EMP_ID** scalar functions, in the dbo schema, which takes the employee designation as a parameter and returns an employee ID (integer).</span></span>  
  
```  
public partial class ScalarFunctions_dboClient : System.ServiceModel.ClientBase<ScalarFunctions_dbo>, ScalarFunctions_dbo {      
    public System.Nullable<int> GET_EMP_ID(string emp_desig);  
}  
```  
  
 <span data-ttu-id="0b876-133">在此程式碼片段， **ScalarFunctions_dboClient**是 WCF 中的類別所產生的 SqlAdapterBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b876-133">In this snippet, **ScalarFunctions_dboClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-invoking-scalar-functions"></a><span data-ttu-id="0b876-134">叫用純量函數的參數</span><span class="sxs-lookup"><span data-stu-id="0b876-134">Parameters for Invoking Scalar Functions</span></span>  
 <span data-ttu-id="0b876-135">所公開的方法的參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用純量函式會在 SQL Server 純量函式定義中定義的參數相同。</span><span class="sxs-lookup"><span data-stu-id="0b876-135">The parameters for the methods exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke a scalar function are the same as the parameters defined in the scalar function definition in SQL Server.</span></span> <span data-ttu-id="0b876-136">例如，叫用 GET_EMP_ID 純量函式的參數是 emp_desig，而可員工的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b876-136">For example, the parameter for invoking the GET_EMP_ID scalar function is emp_desig and takes an employee’s designation.</span></span>  
  
 <span data-ttu-id="0b876-137">同樣地，純量函數的傳回值是與 SQL Server 純量函式定義中定義的傳回值相同。</span><span class="sxs-lookup"><span data-stu-id="0b876-137">Again, the return value for a scalar function is same as the return value defined in the scalar function definition in SQL Server.</span></span> <span data-ttu-id="0b876-138">比方說，GET_EMP_ID 函式的傳回值是整數類型的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b876-138">For example, the return value for the GET_EMP_ID function is an employee’s ID of type integer.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-scalar-functions"></a><span data-ttu-id="0b876-139">建立 WCF 用戶端來叫用純量函數</span><span class="sxs-lookup"><span data-stu-id="0b876-139">Creating a WCF Client to Invoke Scalar Functions</span></span>  
 <span data-ttu-id="0b876-140">使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-140">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="0b876-141">本章節描述如何建立 WCF 用戶端來叫用**GET_EMP_ID**純量函數。</span><span class="sxs-lookup"><span data-stu-id="0b876-141">This section describes how to create a WCF client to invoke the **GET_EMP_ID** scalar function.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="0b876-142">若要建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="0b876-142">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="0b876-143">Visual C# 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b876-143">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="0b876-144">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b876-144">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="0b876-145">產生 WCF 用戶端類別**GET_EMP_ID**純量函數。</span><span class="sxs-lookup"><span data-stu-id="0b876-145">Generate the WCF client class for the **GET_EMP_ID** scalar function.</span></span> <span data-ttu-id="0b876-146">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-146">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="0b876-147">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="0b876-147">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="0b876-148">開啟 Program.cs，並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="0b876-148">Open the Program.cs and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              ScalarFunctions_dboClient client = new ScalarFunctions_dboClient("SqlAdapterBinding_ScalarFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="0b876-149">在此程式碼片段， `ScalarFunctions_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="0b876-149">In this snippet, `ScalarFunctions_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="0b876-150">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b876-150">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="0b876-151">`SqlAdapterBinding_ScalarFunctions_dbo`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="0b876-151">`SqlAdapterBinding_ScalarFunctions_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b876-152">在此片段中，您從組態檔使用的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="0b876-152">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="0b876-153">您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="0b876-153">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="0b876-154">如需有關不同的方式，然後指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0b876-154">For more information on the different ways of specifying then client binding, see [Configure  a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="0b876-155">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="0b876-155">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="0b876-156">叫用**GET_EMP_ID**函式來擷取與指定為 「 經理 」 員工的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b876-156">Invoke the **GET_EMP_ID** function to retrieve the ID for an employee with the designation as “Manager”.</span></span>  
  
    ```  
    Console.WriteLine("Invoking the GET_EMP_ID function");  
    string emp_designation = "Manager";  
    try  
    {  
          System.Nullable<int> emp_id = client.GET_EMP_ID(emp_designation);  
          Console.WriteLine("The Employee ID for the employee with 'Manager' designation is:" + emp_id);  
    }  
    catch (Exception e)  
    {  
          Console.WriteLine("Exception: " + e.Message);  
          throw;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0b876-157">為了簡單起見，**員工**資料表有只有一個具有 「 管理員 」 指定的員工。</span><span class="sxs-lookup"><span data-stu-id="0b876-157">For the sake of simplicity, the **Employee** table has only one employee with “Manager” designation.</span></span> <span data-ttu-id="0b876-158">如果目標資料表有多個具有相同指定員工，您必須據以定義函式。</span><span class="sxs-lookup"><span data-stu-id="0b876-158">If your target table has more employees with the same designation, you must define the function accordingly.</span></span>  
  
7.  <span data-ttu-id="0b876-159">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="0b876-159">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="0b876-160">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="0b876-160">Build the project and then run it.</span></span> <span data-ttu-id="0b876-161">應用程式會顯示具有 「 管理員 」 指定員工的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b876-161">The application displays the employee ID of the employee with the designation of “Manager”.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b876-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b876-162">See Also</span></span>  
[<span data-ttu-id="0b876-163">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="0b876-163">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)