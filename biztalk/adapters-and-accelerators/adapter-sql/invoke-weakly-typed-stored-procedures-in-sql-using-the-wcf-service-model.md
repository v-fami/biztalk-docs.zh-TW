---
title: 叫用弱型別預存程序在 SQL 中使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf74a40-4c03-4a4a-9b91-c21babe154fa
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cc2e477aaf5ee113f6479559c23d184e91d905f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012071"
---
# <a name="invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="be4b9-102">叫用弱型別預存程序中使用 WCF 服務模型的 SQL</span><span class="sxs-lookup"><span data-stu-id="be4b9-102">Invoke Weakly-typed Stored Procedures in SQL using the WCF Service Model</span></span>
<span data-ttu-id="be4b9-103">當您叫用底下所列的程序**程序**中的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，輸出是資料集陣列的形式。</span><span class="sxs-lookup"><span data-stu-id="be4b9-103">When you invoke a procedure listed under the **Procedures** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], the output is in the form of a DataSet array.</span></span> <span data-ttu-id="be4b9-104">本主題提供有關如何建立 WCF 用戶端來叫用傳回的資料集陣列的 SQL Server 中的預存程序的指示。</span><span class="sxs-lookup"><span data-stu-id="be4b9-104">This topic provides instructions on how to create a WCF client to invoke a stored procedure in SQL Server that returns a DataSet array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be4b9-105">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。</span><span class="sxs-lookup"><span data-stu-id="be4b9-105">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="be4b9-106">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="be4b9-106">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="be4b9-107">本主題中的範例使用 GET_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-107">The example in this topic uses the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="be4b9-108">此預存程序會採用員工識別碼做為輸入參數，並傳回具有該識別碼之員工的所有對應的資料行</span><span class="sxs-lookup"><span data-stu-id="be4b9-108">This stored procedure takes an employee ID as an input parameter and returns all the corresponding columns for the employee with that ID.</span></span> <span data-ttu-id="be4b9-109">GET_EMP_DETAILS 預存程序會建立執行 SQL 指令碼提供範例。</span><span class="sxs-lookup"><span data-stu-id="be4b9-109">The GET_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="be4b9-110">如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="be4b9-110">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="be4b9-111">範例中， **Execute_StoredProc**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="be4b9-111">A sample, **Execute_StoredProc**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="be4b9-112">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="be4b9-112">The WCF Client Class</span></span>  
 <span data-ttu-id="be4b9-113">叫用預存程序，在產生 WCF 用戶端的名稱**程序**節點使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會列在下表。</span><span class="sxs-lookup"><span data-stu-id="be4b9-113">The name of the WCF client generated for invoking stored procedures under the **Procedures** node using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="be4b9-114">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="be4b9-114">SQL Server Database Artifact</span></span>|<span data-ttu-id="be4b9-115">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="be4b9-115">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="be4b9-116">程序 (底下**程序**節點)</span><span class="sxs-lookup"><span data-stu-id="be4b9-116">Procedure (under the **Procedures** node)</span></span>|<span data-ttu-id="be4b9-117">Procedures_ [schema] 用戶端</span><span class="sxs-lookup"><span data-stu-id="be4b9-117">Procedures_[schema]Client</span></span>|  
  
 <span data-ttu-id="be4b9-118">[結構描述] 是所屬的結構描述的程序;例如"dbo"時。</span><span class="sxs-lookup"><span data-stu-id="be4b9-118">[schema] is the schema to which the procedure belongs; for example “dbo”.</span></span>  
  
### <a name="method-signature-for-invoking-stored-procedures"></a><span data-ttu-id="be4b9-119">叫用預存程序的方法簽章</span><span class="sxs-lookup"><span data-stu-id="be4b9-119">Method Signature for Invoking Stored Procedures</span></span>  
 <span data-ttu-id="be4b9-120">下表顯示要叫用預存程序所公開的方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="be4b9-120">The following table shows the signature for the method exposed to invoke the stored procedures.</span></span>  
  
|<span data-ttu-id="be4b9-121">作業</span><span class="sxs-lookup"><span data-stu-id="be4b9-121">Operation</span></span>|<span data-ttu-id="be4b9-122">方法簽章</span><span class="sxs-lookup"><span data-stu-id="be4b9-122">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="be4b9-123">程序名稱</span><span class="sxs-lookup"><span data-stu-id="be4b9-123">Procedure name</span></span>|<span data-ttu-id="be4b9-124">System.Data.DataSet [] [程序名稱] (參數 1，參數 2，...\)</span><span class="sxs-lookup"><span data-stu-id="be4b9-124">System.Data.DataSet[] [procedure_name](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="be4b9-125">[程序名稱] 是程序; 名稱比方說 GET_EMP_DETAILS</span><span class="sxs-lookup"><span data-stu-id="be4b9-125">[procedure_name] is the name of the procedure; for example GET_EMP_DETAILS</span></span>  
  
 <span data-ttu-id="be4b9-126">例如，下列程式碼片段顯示 GET_EMP_DETAILS 程序的叫用方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="be4b9-126">As an example, the signature for the method to invoke the GET_EMP_DETAILS procedure is shown in the following code snippet.</span></span>  
  
```  
public partial class Procedures_dboClient : System.ServiceModel.ClientBase<Procedures_dbo>, Procedures_dbo {  
  public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 <span data-ttu-id="be4b9-127">在此片段中，</span><span class="sxs-lookup"><span data-stu-id="be4b9-127">In this snippet,</span></span>  
  
-   <span data-ttu-id="be4b9-128">`Procedures_dboClient` 是 WCF 用戶端類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="be4b9-128">`Procedures_dboClient` is the name of the WCF client class.</span></span> <span data-ttu-id="be4b9-129">在此範例中，您可以使用這個類別來建立用戶端來叫用預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-129">In this example, you use this class to create a client to invoke the stored procedure.</span></span>  
  
-   <span data-ttu-id="be4b9-130">`public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` 是您在此範例中，叫用的方法來叫用預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-130">`public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` is the method that you invoke in this example to invoke the stored procedure.</span></span> <span data-ttu-id="be4b9-131">這個預存程序會採用員工識別碼，並傳回資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="be4b9-131">This stored procedure takes an employee ID and returns a DataSet array.</span></span>  
  
## <a name="create-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a><span data-ttu-id="be4b9-132">建立 WCF 用戶端叫用 SQL Server 中的預存程序</span><span class="sxs-lookup"><span data-stu-id="be4b9-132">Create a WCF Client to Invoke a Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="be4b9-133">一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[配接器的 WCF 服務模型的概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="be4b9-133">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="be4b9-134">本節特別說明如何建立 WCF 用戶端叫用預存程序的結果集資料集的陣列。</span><span class="sxs-lookup"><span data-stu-id="be4b9-134">This section specifically describes how to create a WCF client that invokes a stored procedure, the result set for which is a DataSet array.</span></span> <span data-ttu-id="be4b9-135">在本主題中，例如，您叫用 GET_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-135">In this topic, as an example, you invoke the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="be4b9-136">這個預存程序會建立執行 SQL 指令碼提供每個範例。</span><span class="sxs-lookup"><span data-stu-id="be4b9-136">This stored procedure is created by running the SQL script provided with each sample.</span></span>  
  
  
1. <span data-ttu-id="be4b9-137">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="be4b9-137">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="be4b9-138">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="be4b9-138">For this topic, create a console application.</span></span>  
  
2. <span data-ttu-id="be4b9-139">產生 WCF 用戶端類別，如 GET_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-139">Generate the WCF client class for the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="be4b9-140">請確定您選取下的程序**程序**節點。</span><span class="sxs-lookup"><span data-stu-id="be4b9-140">Make sure you select the procedure under the **Procedures** node.</span></span> <span data-ttu-id="be4b9-141">如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="be4b9-141">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="be4b9-142">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="be4b9-142">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3. <span data-ttu-id="be4b9-143">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="be4b9-143">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4. <span data-ttu-id="be4b9-144">開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="be4b9-144">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
   ```  
  
             Procedures_dboClient client = new Procedures_dboClient("SqlAdapterBinding_Procedures_dbo");  
  
   client.ClientCredentials.UserName.UserName = "<Enter username here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  
  
    <span data-ttu-id="be4b9-145">在此片段中， `Procedures_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="be4b9-145">In this snippet, `Procedures_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="be4b9-146">此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="be4b9-146">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="be4b9-147">`SqlAdapterBinding_Procedures_dbo` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="be4b9-147">`SqlAdapterBinding_Procedures_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="be4b9-148">在此片段中，您使用的繫結和端點位址從組態檔。</span><span class="sxs-lookup"><span data-stu-id="be4b9-148">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="be4b9-149">您也可以明確指定這些值在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="be4b9-149">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="be4b9-150">如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="be4b9-150">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5. <span data-ttu-id="be4b9-151">下列程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="be4b9-151">Open the client as described in the snippet below:</span></span>  
  
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
  
6. <span data-ttu-id="be4b9-152">叫用 GET_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="be4b9-152">Invoke the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="be4b9-153">您可以叫用 GET_EMP_DETAILS 程序之前，您必須新增`System.Data`您的程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="be4b9-153">Before you invoke the GET_EMP_DETAILS procedure, you must add the `System.Data` namespace to your code.</span></span>  
  
   ```  
   DataSet[] dataArray;  
   int returnCode;  
  
   try  
   {  
      Console.WriteLine("Calling a stored procedure...");  
      dataArray = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   Console.WriteLine("The details for the employee with ID '10001' are:");  
   Console.WriteLine("*************************************************");  
  
   foreach (DataSet dataSet in dataArray)  
   {  
      foreach (DataTable tab in dataArray[0].Tables)  
      {  
         foreach (DataRow row in tab.Rows)  
         {  
            for (int i = 0; i < tab.Columns.Count; i++)  
            {  
               Console.WriteLine(row[i]);  
            }  
         }  
      }  
   }  
   Console.WriteLine("*************************************************");  
  
   ```  
  
7. <span data-ttu-id="be4b9-154">下列程式碼片段中所述，請關閉該用戶端：</span><span class="sxs-lookup"><span data-stu-id="be4b9-154">Close the client as described in the snippet below:</span></span>  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
8. <span data-ttu-id="be4b9-155">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="be4b9-155">Build the project and then run it.</span></span> <span data-ttu-id="be4b9-156">員工，為哪些您提取要求詳細資料</span><span class="sxs-lookup"><span data-stu-id="be4b9-156">The details for the employee, for which you pr</span></span>
9. <span data-ttu-id="be4b9-157">ovided 識別碼，會顯示在主控台上。</span><span class="sxs-lookup"><span data-stu-id="be4b9-157">ovided the ID, are displayed on the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4b9-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be4b9-158">See Also</span></span>  
[<span data-ttu-id="be4b9-159">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="be4b9-159">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)