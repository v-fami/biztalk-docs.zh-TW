---
title: 使用 WCF 服務模型叫用 SQL Server 中的資料表值函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48688bcc-36b4-4cc1-b078-17e7a5e1cf8c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4243973f6e6b04cddec14261d5b1acedff4b9e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989159"
---
# <a name="invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model"></a><span data-ttu-id="a0d17-102">使用 WCF 服務模型叫用 SQL Server 中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="a0d17-102">Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model</span></span>
<span data-ttu-id="a0d17-103">您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在.NET 應用程式中使用 WCF 服務模型，來叫用 SQL Server 中的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="a0d17-103">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET application using the WCF service model to invoke table-valued functions in SQL Server.</span></span> <span data-ttu-id="a0d17-104">配接器會公開的資料表值函式為可以直接在 SQL Server 叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="a0d17-104">The adapter exposes the table-valued functions as methods that can be invoked directly on SQL Server.</span></span> <span data-ttu-id="a0d17-105">如需配接器如何支援純量函式的詳細資訊，請參閱[Execute Table-Valued 函式中使用 SQL 配接器的 SQL Server](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-105">For more information about how the adapter supports scalar functions, see [Execute Table-Valued Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="a0d17-106">本主題示範如何叫用 TVF_EMPLOYEE 函式，SQL Server 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a0d17-106">This topic demonstrates how to invoke the TVF_EMPLOYEE function in a SQL Server database.</span></span> <span data-ttu-id="a0d17-107">TVF_EMPLOYEE 函式中的員工的表示法**員工**資料表，並傳回記錄的員工。</span><span class="sxs-lookup"><span data-stu-id="a0d17-107">The TVF_EMPLOYEE function takes the designation of an employee in the **Employee** table and returns the record for the employee.</span></span> <span data-ttu-id="a0d17-108">TVF_EMPLOYEE 函式和**員工**執行提供的範例 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="a0d17-108">The TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="a0d17-109">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-109">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="a0d17-110">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="a0d17-110">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="a0d17-111">本主題中的範例上叫用 TVF_EMPLOYEE 資料表值函式**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="a0d17-111">The example in this topic invoked the TVF_EMPLOYEE table-valued function on the **Employee** table.</span></span> <span data-ttu-id="a0d17-112">TVF_EMPLOYEE 函式和**員工**執行提供的範例 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="a0d17-112">TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="a0d17-113">範例中， **TableFunction_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a0d17-113">A sample, **TableFunction_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span> <span data-ttu-id="a0d17-114">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-114">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="a0d17-115">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="a0d17-115">The WCF Client Class</span></span>  
 <span data-ttu-id="a0d17-116">叫用純量函式，在 SQL Server 中使用產生的 WCF 用戶端名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會列在下表。</span><span class="sxs-lookup"><span data-stu-id="a0d17-116">The name of the WCF client generated for invoking the scalar function in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="a0d17-117">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="a0d17-117">SQL Server Database Artifact</span></span>|<span data-ttu-id="a0d17-118">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="a0d17-118">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="a0d17-119">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="a0d17-119">Table-valued function</span></span>|<span data-ttu-id="a0d17-120">TableValuedFunctions_ [SCHEMA] 用戶端</span><span class="sxs-lookup"><span data-stu-id="a0d17-120">TableValuedFunctions_[SCHEMA]Client</span></span>|  
  
 <span data-ttu-id="a0d17-121">[SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。</span><span class="sxs-lookup"><span data-stu-id="a0d17-121">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-table-valued-functions"></a><span data-ttu-id="a0d17-122">叫用資料表值函式的方法簽章</span><span class="sxs-lookup"><span data-stu-id="a0d17-122">Method Signature for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="a0d17-123">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="a0d17-123">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="a0d17-124">簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。</span><span class="sxs-lookup"><span data-stu-id="a0d17-124">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="a0d17-125">作業</span><span class="sxs-lookup"><span data-stu-id="a0d17-125">Operation</span></span>|<span data-ttu-id="a0d17-126">方法簽章</span><span class="sxs-lookup"><span data-stu-id="a0d17-126">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="a0d17-127">資料表值函式名稱</span><span class="sxs-lookup"><span data-stu-id="a0d17-127">Table-valued function name</span></span>|<span data-ttu-id="a0d17-128">公用 [NAMESPACE] [FUNCTION_NAME] [] [FUNCTION_NAME] (參數 1，參數 2，...\)</span><span class="sxs-lookup"><span data-stu-id="a0d17-128">public [NAMESPACE][FUNCTION_NAME][] [FUNCTION_NAME](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="a0d17-129">[NAMESPACE] = 命名空間，例如 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span><span class="sxs-lookup"><span data-stu-id="a0d17-129">[NAMESPACE] = The namespace, for example, schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span></span>  
  
 <span data-ttu-id="a0d17-130">[FUNCTION_NAME] = 資料表值函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d17-130">[FUNCTION_NAME] = Name of the table-valued function.</span></span>  
  
 <span data-ttu-id="a0d17-131">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**TVF_EMPLOYEE** dbo 結構描述，它會做為參數指定的員工，並傳回該員工中的純量函式資料錄。</span><span class="sxs-lookup"><span data-stu-id="a0d17-131">As an example, the following code shows the method signatures for a WCF client class generated for the **TVF_EMPLOYEE** scalar functions, in the dbo schema, which takes the employee designation as a parameter and returns the employee record.</span></span>  
  
```  
public partial class TableValuedFunctions_dboClient : System.ServiceModel.ClientBase<TableValuedFunctions_dbo>, TableValuedFunctions_dbo {      
    public schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] TVF_EMPLOYEE(string emp_desig);  
}  
```  
  
 <span data-ttu-id="a0d17-132">在此片段中， **TableValuedFunctions_dboClient**是 WCF 中類別的名稱所產生 SqlAdapterBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0d17-132">In this snippet, **TableValuedFunctions_dboClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-invoking-table-valued-functions"></a><span data-ttu-id="a0d17-133">叫用資料表值函式的參數</span><span class="sxs-lookup"><span data-stu-id="a0d17-133">Parameters for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="a0d17-134">所公開的方法的參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用資料表值函式會在 SQL Server 中的函式定義中定義的參數相同。</span><span class="sxs-lookup"><span data-stu-id="a0d17-134">The parameters for the methods exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke a table-valued function are the same as the parameters defined in the function definition in SQL Server.</span></span> <span data-ttu-id="a0d17-135">例如，叫用 TVF_EMPLOYEE 資料表值函式的參數是 emp_desig，而會採用員工的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d17-135">For example, the parameter for invoking the TVF_EMPLOYEE table-valued function is emp_desig and takes an employee’s designation.</span></span>  
  
 <span data-ttu-id="a0d17-136">同樣地，對於資料表值函式的傳回值，等於是在 SQL Server 中的函式定義中的傳回值。</span><span class="sxs-lookup"><span data-stu-id="a0d17-136">Again, the return value for a table-valued function is same as the return value defined in the function definition in SQL Server.</span></span> <span data-ttu-id="a0d17-137">比方說，TVF_EMPLOYEE 函式的傳回值是陣列的型別 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE [] 的記錄。</span><span class="sxs-lookup"><span data-stu-id="a0d17-137">For example, the return value for the TVF_EMPLOYEE function is an array of records of type schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[].</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-table-valued-functions"></a><span data-ttu-id="a0d17-138">建立 WCF 用戶端叫用資料表值函式</span><span class="sxs-lookup"><span data-stu-id="a0d17-138">Creating a WCF Client to Invoke Table-valued Functions</span></span>  
 <span data-ttu-id="a0d17-139">一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[使用 SQL 配接器的 WCF 服務模型的概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-139">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="a0d17-140">本節說明如何建立 WCF 用戶端來叫用**TVF_EMPLOYEE**資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="a0d17-140">This section describes how to create a WCF client to invoke the **TVF_EMPLOYEE** table-valued function.</span></span>  
  
 
1. <span data-ttu-id="a0d17-141">Visual C# 中建立的專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0d17-141">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)].</span></span> <span data-ttu-id="a0d17-142">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0d17-142">For this topic, create a console application.</span></span>  
  
2. <span data-ttu-id="a0d17-143">產生 WCF 用戶端類別，如**TVF_EMPLOYEE**純量函式。</span><span class="sxs-lookup"><span data-stu-id="a0d17-143">Generate the WCF client class for the **TVF_EMPLOYEE** scalar function.</span></span> <span data-ttu-id="a0d17-144">如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-144">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3. <span data-ttu-id="a0d17-145">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="a0d17-145">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4. <span data-ttu-id="a0d17-146">開啟 Program.cs，並建立用戶端，如下列程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="a0d17-146">Open the Program.cs and create a client as described in the snippet below.</span></span>  
  
   ```  
  
             TableValuedFunctions_dboClient client = new TableValuedFunctions_dboClient("SqlAdapterBinding_TableValuedFunctions_dbo");  
   client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  
  
    <span data-ttu-id="a0d17-147">在此片段中， `TableValuedFunctions_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="a0d17-147">In this snippet, `TableValuedFunctions_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="a0d17-148">此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0d17-148">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="a0d17-149">`SqlAdapterBinding_TableValuedFunctions_dbo` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="a0d17-149">`SqlAdapterBinding_TableValuedFunctions_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a0d17-150">在此片段中，您使用的繫結和端點位址從組態檔。</span><span class="sxs-lookup"><span data-stu-id="a0d17-150">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="a0d17-151">您也可以明確指定這些值在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0d17-151">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="a0d17-152">如需有關不同的方式，然後指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d17-152">For more information on the different ways of specifying then client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5. <span data-ttu-id="a0d17-153">下列程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="a0d17-153">Open the client as described in the snippet below:</span></span>  
  
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
  
6. <span data-ttu-id="a0d17-154">叫用**TVF_EMPLOYEE**函式來擷取具有 「 管理員 」 指定的所有員工記錄。</span><span class="sxs-lookup"><span data-stu-id="a0d17-154">Invoke the **TVF_EMPLOYEE** function to retrieve all the employee records having the “Manager” designation.</span></span>  
  
   ```  
   Console.WriteLine("Invoking the TVF_EMPLOYEE function");  
   schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] emp_details;  
   string emp_designation = "Manager";  
  
   try  
   {  
       emp_details = client.TVF_EMPLOYEE(emp_designation);  
   }  
   catch (Exception e)  
   {  
       Console.WriteLine("Exception: " + e.Message);  
       throw;  
   }  
   Console.WriteLine("The details for the employee with the 'Manager' designation are:");  
   Console.WriteLine("*******************************************************************");  
   for (int i = 0; i < emp_details.Length; i++)  
   {  
       Console.WriteLine("Employee ID        : " + emp_details[i].Employee_ID);  
       Console.WriteLine("Employee Name      : " + emp_details[i].Name);  
       Console.WriteLine("Employee Desigation: " + emp_details[i].Designation);  
       Console.WriteLine("Employee Salary    : " + emp_details[i].Salary);  
       Console.WriteLine();  
   }  
   ```  
  
7. <span data-ttu-id="a0d17-155">下列程式碼片段中所述，請關閉該用戶端：</span><span class="sxs-lookup"><span data-stu-id="a0d17-155">Close the client as described in the snippet below:</span></span>  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
8. <span data-ttu-id="a0d17-156">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="a0d17-156">Build the project and then run it.</span></span> <span data-ttu-id="a0d17-157">員工識別碼、 名稱和具有 「 管理員 」 指定的所有員工的薪資，則會顯示應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0d17-157">The application displays the employee ID, name, and salary of all the employees with a “Manager” designation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d17-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0d17-158">See Also</span></span>  
[<span data-ttu-id="a0d17-159">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="a0d17-159">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)