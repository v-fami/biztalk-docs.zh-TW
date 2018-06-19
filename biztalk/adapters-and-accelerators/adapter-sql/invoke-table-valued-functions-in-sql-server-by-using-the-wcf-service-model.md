---
title: 使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式 |Microsoft 文件
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
ms.openlocfilehash: a736a82e57f71568f8718a6e4d41e7b649004120
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224694"
---
# <a name="invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model"></a><span data-ttu-id="73fa8-102">使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="73fa8-102">Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model</span></span>
<span data-ttu-id="73fa8-103">您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].NET 應用程式使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式中。</span><span class="sxs-lookup"><span data-stu-id="73fa8-103">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET application using the WCF service model to invoke table-valued functions in SQL Server.</span></span> <span data-ttu-id="73fa8-104">配接器會將資料表值函式公開為可直接在 SQL Server 叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="73fa8-104">The adapter exposes the table-valued functions as methods that can be invoked directly on SQL Server.</span></span> <span data-ttu-id="73fa8-105">如需配接器如何支援純量函數的詳細資訊，請參閱[Execute Table-Valued 函式中使用 SQL 配接器的 SQL Server](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-105">For more information about how the adapter supports scalar functions, see [Execute Table-Valued Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="73fa8-106">本主題示範如何叫用 SQL Server 資料庫中的 TVF_EMPLOYEE 函式。</span><span class="sxs-lookup"><span data-stu-id="73fa8-106">This topic demonstrates how to invoke the TVF_EMPLOYEE function in a SQL Server database.</span></span> <span data-ttu-id="73fa8-107">TVF_EMPLOYEE 函式中的員工的指定**員工**資料表，並傳回員工的記錄。</span><span class="sxs-lookup"><span data-stu-id="73fa8-107">The TVF_EMPLOYEE function takes the designation of an employee in the **Employee** table and returns the record for the employee.</span></span> <span data-ttu-id="73fa8-108">TVF_EMPLOYEE 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="73fa8-108">The TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="73fa8-109">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-109">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="73fa8-110">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="73fa8-110">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="73fa8-111">本主題中的範例上叫用 TVF_EMPLOYEE 資料表值函式**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="73fa8-111">The example in this topic invoked the TVF_EMPLOYEE table-valued function on the **Employee** table.</span></span> <span data-ttu-id="73fa8-112">TVF_EMPLOYEE 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="73fa8-112">TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="73fa8-113">範例中， **TableFunction_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="73fa8-113">A sample, **TableFunction_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span> <span data-ttu-id="73fa8-114">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-114">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="73fa8-115">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="73fa8-115">The WCF Client Class</span></span>  
 <span data-ttu-id="73fa8-116">叫用純量函數中使用 SQL Server 產生 WCF 用戶端的名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]列於下表。</span><span class="sxs-lookup"><span data-stu-id="73fa8-116">The name of the WCF client generated for invoking the scalar function in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="73fa8-117">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="73fa8-117">SQL Server Database Artifact</span></span>|<span data-ttu-id="73fa8-118">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="73fa8-118">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="73fa8-119">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="73fa8-119">Table-valued function</span></span>|<span data-ttu-id="73fa8-120">TableValuedFunctions_ [SCHEMA] 用戶端</span><span class="sxs-lookup"><span data-stu-id="73fa8-120">TableValuedFunctions_[SCHEMA]Client</span></span>|  
  
 <span data-ttu-id="73fa8-121">[SCHEMA] = 集合 SQL Server 成品。例如，dbo。</span><span class="sxs-lookup"><span data-stu-id="73fa8-121">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-table-valued-functions"></a><span data-ttu-id="73fa8-122">方法簽章的叫用資料表值函式</span><span class="sxs-lookup"><span data-stu-id="73fa8-122">Method Signature for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="73fa8-123">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="73fa8-123">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="73fa8-124">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="73fa8-124">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="73fa8-125">作業</span><span class="sxs-lookup"><span data-stu-id="73fa8-125">Operation</span></span>|<span data-ttu-id="73fa8-126">方法簽章</span><span class="sxs-lookup"><span data-stu-id="73fa8-126">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="73fa8-127">資料表值函式名稱</span><span class="sxs-lookup"><span data-stu-id="73fa8-127">Table-valued function name</span></span>|<span data-ttu-id="73fa8-128">公用 [命名空間] [FUNCTION_NAME] [] [FUNCTION_NAME] (參數 1，參數 2，...\)</span><span class="sxs-lookup"><span data-stu-id="73fa8-128">public [NAMESPACE][FUNCTION_NAME][] [FUNCTION_NAME](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="73fa8-129">[命名空間] = 在命名空間，例如 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span><span class="sxs-lookup"><span data-stu-id="73fa8-129">[NAMESPACE] = The namespace, for example, schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span></span>  
  
 <span data-ttu-id="73fa8-130">[FUNCTION_NAME] = 資料表值函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="73fa8-130">[FUNCTION_NAME] = Name of the table-valued function.</span></span>  
  
 <span data-ttu-id="73fa8-131">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**TVF_EMPLOYEE** dbo 結構描述中，做為參數指定的員工，然後傳回員工的純量函數資料錄。</span><span class="sxs-lookup"><span data-stu-id="73fa8-131">As an example, the following code shows the method signatures for a WCF client class generated for the **TVF_EMPLOYEE** scalar functions, in the dbo schema, which takes the employee designation as a parameter and returns the employee record.</span></span>  
  
```  
public partial class TableValuedFunctions_dboClient : System.ServiceModel.ClientBase<TableValuedFunctions_dbo>, TableValuedFunctions_dbo {      
    public schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] TVF_EMPLOYEE(string emp_desig);  
}  
```  
  
 <span data-ttu-id="73fa8-132">在此程式碼片段， **TableValuedFunctions_dboClient**是 WCF 中的類別所產生的 SqlAdapterBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73fa8-132">In this snippet, **TableValuedFunctions_dboClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-invoking-table-valued-functions"></a><span data-ttu-id="73fa8-133">叫用資料表值函式的參數</span><span class="sxs-lookup"><span data-stu-id="73fa8-133">Parameters for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="73fa8-134">所公開的方法的參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用資料表值函式會在 SQL Server 中的函式定義中定義的參數相同。</span><span class="sxs-lookup"><span data-stu-id="73fa8-134">The parameters for the methods exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke a table-valued function are the same as the parameters defined in the function definition in SQL Server.</span></span> <span data-ttu-id="73fa8-135">例如，叫用 TVF_EMPLOYEE 資料表值函式的參數是 emp_desig，會採用員工的指定。</span><span class="sxs-lookup"><span data-stu-id="73fa8-135">For example, the parameter for invoking the TVF_EMPLOYEE table-valued function is emp_desig and takes an employee’s designation.</span></span>  
  
 <span data-ttu-id="73fa8-136">同樣地，資料表值函式的傳回值是與 SQL Server 中的函式定義中所定義的傳回值相同。</span><span class="sxs-lookup"><span data-stu-id="73fa8-136">Again, the return value for a table-valued function is same as the return value defined in the function definition in SQL Server.</span></span> <span data-ttu-id="73fa8-137">比方說，TVF_EMPLOYEE 函式的傳回值是陣列的型別 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE [] 的記錄。</span><span class="sxs-lookup"><span data-stu-id="73fa8-137">For example, the return value for the TVF_EMPLOYEE function is an array of records of type schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[].</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-table-valued-functions"></a><span data-ttu-id="73fa8-138">建立 WCF 用戶端來叫用資料表值函式</span><span class="sxs-lookup"><span data-stu-id="73fa8-138">Creating a WCF Client to Invoke Table-valued Functions</span></span>  
 <span data-ttu-id="73fa8-139">使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-139">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="73fa8-140">本章節描述如何建立 WCF 用戶端來叫用**TVF_EMPLOYEE**資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="73fa8-140">This section describes how to create a WCF client to invoke the **TVF_EMPLOYEE** table-valued function.</span></span>  
  
 
1.  <span data-ttu-id="73fa8-141">Visual C# 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73fa8-141">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)].</span></span> <span data-ttu-id="73fa8-142">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="73fa8-142">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="73fa8-143">產生 WCF 用戶端類別**TVF_EMPLOYEE**純量函數。</span><span class="sxs-lookup"><span data-stu-id="73fa8-143">Generate the WCF client class for the **TVF_EMPLOYEE** scalar function.</span></span> <span data-ttu-id="73fa8-144">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-144">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="73fa8-145">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="73fa8-145">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="73fa8-146">開啟 Program.cs，並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="73fa8-146">Open the Program.cs and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableValuedFunctions_dboClient client = new TableValuedFunctions_dboClient("SqlAdapterBinding_TableValuedFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="73fa8-147">在此程式碼片段， `TableValuedFunctions_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="73fa8-147">In this snippet, `TableValuedFunctions_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="73fa8-148">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73fa8-148">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="73fa8-149">`SqlAdapterBinding_TableValuedFunctions_dbo`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="73fa8-149">`SqlAdapterBinding_TableValuedFunctions_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73fa8-150">在此片段中，您從組態檔使用的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="73fa8-150">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="73fa8-151">您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="73fa8-151">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="73fa8-152">如需有關不同的方式，然後指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="73fa8-152">For more information on the different ways of specifying then client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="73fa8-153">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="73fa8-153">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="73fa8-154">叫用**TVF_EMPLOYEE**函式可擷取具有 「 管理員 」 指定的所有員工記錄。</span><span class="sxs-lookup"><span data-stu-id="73fa8-154">Invoke the **TVF_EMPLOYEE** function to retrieve all the employee records having the “Manager” designation.</span></span>  
  
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
  
7.  <span data-ttu-id="73fa8-155">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="73fa8-155">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="73fa8-156">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="73fa8-156">Build the project and then run it.</span></span> <span data-ttu-id="73fa8-157">員工識別碼、 名稱和具有 「 管理員 」 指定的所有員工的薪資，則會顯示應用程式。</span><span class="sxs-lookup"><span data-stu-id="73fa8-157">The application displays the employee ID, name, and salary of all the employees with a “Manager” designation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fa8-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73fa8-158">See Also</span></span>  
[<span data-ttu-id="73fa8-159">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="73fa8-159">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)