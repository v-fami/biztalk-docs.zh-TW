---
title: "叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e227c60f-f6fe-40bf-bf41-2784a4428ad0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c9ff6b37f2e18c03a364e3f584ea9f79b547f1e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="926a3-102">叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式</span><span class="sxs-lookup"><span data-stu-id="926a3-102">Invoke concurrent programs in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="926a3-103">Oracle E-business Suite 會公開您可以執行特定操作 Oracle 應用程式上的執行的並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-103">Oracle E-Business Suite exposes concurrent programs that you can execute to perform specific operations on Oracle applications.</span></span> <span data-ttu-id="926a3-104">每個 Oracle 應用程式有一組標準的並行程式 （也就是相同的所有作業） 和特定 Oracle 應用程式專屬的並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-104">Each Oracle application has a set of standard concurrent programs (that are same across all operations) and certain concurrent programs that are specific to an Oracle application.</span></span> <span data-ttu-id="926a3-105">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開所有的並行程式做為配接器用戶端可以叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="926a3-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes all concurrent programs as operations that adapter clients can invoke.</span></span> <span data-ttu-id="926a3-106">如需配接器如何支援同時執行之程式的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-106">For more information about how the adapter supports concurrent programs, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="926a3-107">Oracle E-business 配接器不會公開其中繼資料的並行程式，每個這些並行程式可 100 的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="926a3-107">For the concurrent programs that do not expose their metadata, the Oracle E-Business adapter exposes 100 optional parameters for each of these concurrent programs.</span></span> <span data-ttu-id="926a3-108">順利叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，然後將其指定。</span><span class="sxs-lookup"><span data-stu-id="926a3-108">To invoke these concurrent programs successfully, the user must consult the Oracle E-Business Suite documentation to figure out the parameters for a concurrent program that require a value, and then specify them.</span></span> <span data-ttu-id="926a3-109">並行程式的範例是**筆記本的匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-109">An example of such a concurrent program is **Journal Import** (actual name: **GLLEZL**) in the **General Ledger** application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="926a3-110">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="926a3-110">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="926a3-111">本主題中的範例會叫用**MS_SAMPLE_COPY_EMP_DATA**並行程式，後面接著**Get_Status**並行程式知道第一個並行程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="926a3-111">The example in this topic invokes the **MS_SAMPLE_COPY_EMP_DATA** concurrent program, followed by the **Get_Status** concurrent program to know the status of the first concurrent program.</span></span> <span data-ttu-id="926a3-112">這些並行程式會從叫用**應用程式物件程式庫**應用程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-112">These concurrent programs are invoked from the **Application Object Library** application.</span></span> <span data-ttu-id="926a3-113">**MS_SAMPLE_COPY_EMP_DATA**建立執行範例所提供的指令碼。</span><span class="sxs-lookup"><span data-stu-id="926a3-113">The **MS_SAMPLE_COPY_EMP_DATA** is created by running the script provided with the samples.</span></span> <span data-ttu-id="926a3-114">如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-114">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="926a3-115">範例中， **ConcurrentProgram_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="926a3-115">A sample, **ConcurrentProgram_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="926a3-116">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="926a3-116">The WCF Client Class</span></span>  
 <span data-ttu-id="926a3-117">叫用同時執行之程式所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]列於下表。</span><span class="sxs-lookup"><span data-stu-id="926a3-117">The name of the WCF client generated for invoking the concurrent programs by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="926a3-118">成品</span><span class="sxs-lookup"><span data-stu-id="926a3-118">Artifact</span></span>|<span data-ttu-id="926a3-119">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="926a3-119">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="926a3-120">並行程式</span><span class="sxs-lookup"><span data-stu-id="926a3-120">Concurrent Program</span></span>|<span data-ttu-id="926a3-121">ConcurrentPrograms_ [APP_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="926a3-121">ConcurrentPrograms_[APP_NAME]Client</span></span>|  
  
 <span data-ttu-id="926a3-122">[APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。</span><span class="sxs-lookup"><span data-stu-id="926a3-122">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
### <a name="method-signature-for-invoking-concurrent-programs"></a><span data-ttu-id="926a3-123">叫用同時執行之程式的方法簽章</span><span class="sxs-lookup"><span data-stu-id="926a3-123">Method Signature for Invoking Concurrent Programs</span></span>  
 <span data-ttu-id="926a3-124">下表顯示並行程式的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="926a3-124">The following table shows the method signature for the concurrent programs.</span></span>  
  
|<span data-ttu-id="926a3-125">作業</span><span class="sxs-lookup"><span data-stu-id="926a3-125">Operation</span></span>|<span data-ttu-id="926a3-126">方法簽章</span><span class="sxs-lookup"><span data-stu-id="926a3-126">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="926a3-127">並行程式</span><span class="sxs-lookup"><span data-stu-id="926a3-127">Concurrent program</span></span>|<span data-ttu-id="926a3-128">公用\<傳回型別\>< Concurrent_program_name > （參數 1，參數 2，...）</span><span class="sxs-lookup"><span data-stu-id="926a3-128">public \<return type\> <Concurrent_program_name>(param 1, param 2, …)</span></span>|  
  
 <span data-ttu-id="926a3-129">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-129">As an example, the following code shows the method signatures for a WCF client class generated for the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
```  
public partial class ConcurrentPrograms_FNDClient : System.ServiceModel.ClientBase<ConcurrentPrograms_FND>, ConcurrentPrograms_FND {      
  
    public string MS_SAMPLE_COPY_EMP_DATA(schemas.microsoft.com.OracleEBS._2008._05.Options.SetOptions SetOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,  
      string Description, string StartTime);  
  
    public bool GetStatusForConcurrentProgram(string RequestId, out string Phase, out string Status,  
      out string DevPhase, out string DevStatus, out string Message);  
}  
```  
  
 <span data-ttu-id="926a3-130">在此程式碼片段， **ConcurrentPrograms_FNDClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="926a3-130">In this snippet, **ConcurrentPrograms_FNDClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="926a3-131">**MS_SAMPLE_COPY_EMP_DATA**並行程式的叫用方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="926a3-131">**MS_SAMPLE_COPY_EMP_DATA** is the name of the method to invoke the concurrent program.</span></span> <span data-ttu-id="926a3-132">**GetStatusForConcurrentProgram**並行程式來取得第一次的並行處理程式狀態的叫用方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="926a3-132">**GetStatusForConcurrentProgram** is the name of the method to invoke the concurrent program to get the status of the first concurrent program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="926a3-133">**GetStatusForConcurrentProgram**的實際名稱**Get_Status**並行處理程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-133">**GetStatusForConcurrentProgram** is the actual name of the **Get_Status** concurrent program.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-concurrent-programs"></a><span data-ttu-id="926a3-134">建立 WCF 用戶端來叫用同時執行的程式</span><span class="sxs-lookup"><span data-stu-id="926a3-134">Creating a WCF Client to Invoke Concurrent Programs</span></span>  
 <span data-ttu-id="926a3-135">Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-135">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="926a3-136">本章節描述如何建立 WCF 用戶端來叫用**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-136">This section describes how to create a WCF client to invoke the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="926a3-137">若要建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="926a3-137">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="926a3-138">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="926a3-138">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="926a3-139">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-139">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="926a3-140">產生 WCF 用戶端類別**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-140">Generate the WCF client class for the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span> <span data-ttu-id="926a3-141">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-141">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="926a3-142">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="926a3-142">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="926a3-143">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="926a3-143">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="926a3-144">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="926a3-144">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="926a3-145">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="926a3-145">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    ConcurrentPrograms_FNDClient client = new ConcurrentPrograms_FNDClient(binding, address);  
    ```  
  
     <span data-ttu-id="926a3-146">在此程式碼片段， `ConcurrentPrograms_FNDClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="926a3-146">In this snippet, `ConcurrentPrograms_FNDClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="926a3-147">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="926a3-147">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="926a3-148">在此片段中，您明確指定的繫結與端點位址的應用程式程式碼中。</span><span class="sxs-lookup"><span data-stu-id="926a3-148">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="926a3-149">您也可以使用這些值從應用程式組態檔 app.config，也是由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="926a3-149">You can also use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="926a3-150">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-150">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="926a3-151">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="926a3-151">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="926a3-152">因為您叫用 Oracle E-business Suite 應用程式中的並行程式，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="926a3-152">Because you are invoking concurrent programs in an Oracle E-Business Suite application, you must set the application context.</span></span> <span data-ttu-id="926a3-153">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="926a3-153">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="926a3-154">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="926a3-154">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="926a3-155">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="926a3-155">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="926a3-156">叫用**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-156">Invoke the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
    ```  
    string RequestID;  
    bool Result;  
    string Phase;  
    string Status;  
    string DevPhase;  
    string DevStatus;  
    string Message;  
  
    try  
    {  
        Console.WriteLine("Invoking the MS_SAMPLE_COPY_EMP_DATA concurrent program");  
        RequestID = client.MS_SAMPLE_COPY_EMP_DATA(null, null, null, null, null);  
        Console.WriteLine("The request ID generated for the concurrent program is : " + RequestID);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nWaiting for 60 seconds for the concurrent program to be complete");  
        System.Threading.Thread.Sleep(60000);  
        Console.WriteLine("\nInvoking the Get_Status concurrent program");  
        Result = client.GetStatusForConcurrentProgram(RequestID, out Phase, out Status, out DevPhase, out DevStatus, out Message);  
        Console.WriteLine("\nResult is  : " + Result);  
        Console.WriteLine("Phase is     : " + Phase);  
        Console.WriteLine("Status is    : " + Status);  
        Console.WriteLine("DevPhase is  : " + DevPhase);  
        Console.WriteLine("DevStatus is : " + DevStatus);  
        Console.WriteLine("Message is   : " + Message);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;                 
    }  
    ```  
  
10. <span data-ttu-id="926a3-157">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="926a3-157">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    ```  
  
11. <span data-ttu-id="926a3-158">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="926a3-158">Build the project and then run it.</span></span> <span data-ttu-id="926a3-159">應用程式會叫用**MS_SAMPLE_COPY_EMP_DATA**並傳回要求的識別碼。</span><span class="sxs-lookup"><span data-stu-id="926a3-159">The application invokes the **MS_SAMPLE_COPY_EMP_DATA** and returns a request ID.</span></span> <span data-ttu-id="926a3-160">識別碼會傳遞至**Get_Status**並行程式，最後會提供狀態**MS_SAMPLE_COPY_EMP_DATA**資料行的程式。</span><span class="sxs-lookup"><span data-stu-id="926a3-160">The ID is then passed to the **Get_Status** concurrent program, which finally provides the status of the **MS_SAMPLE_COPY_EMP_DATA** column program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926a3-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="926a3-161">See Also</span></span>  
 [<span data-ttu-id="926a3-162">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="926a3-162">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)