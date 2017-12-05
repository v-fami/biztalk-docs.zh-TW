---
title: "叫用 Oracle E-business Suite 使用 WCF 服務模型中的要求集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb6ec551-c069-4133-add5-2ba83d20405d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec243c1d1ed1093241e4dc6120c3703fbf2e4542
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="7427e-102">叫用要求集 Oracle E-business Suite 使用 WCF 服務模型中</span><span class="sxs-lookup"><span data-stu-id="7427e-102">Invoke request sets in Oracle E-Business Suite using the WCF service model</span></span>
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="7427e-103">可讓您執行 Oracle E-business Suite 中要求集合。</span><span class="sxs-lookup"><span data-stu-id="7427e-103"> enables you to execute request sets in Oracle E-Business Suite.</span></span> <span data-ttu-id="7427e-104">要求集劃分為一個或多個階段，而且每個階段包含一組報表和並行程式。</span><span class="sxs-lookup"><span data-stu-id="7427e-104">Request sets are divided into one or more stages, and each stage contains a set of reports and concurrent programs.</span></span> <span data-ttu-id="7427e-105">如需如何配接器支援要求的詳細資訊，請參閱[上設定要求的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7427e-105">For more information about how the adapter supports request sets, see [Operations on Request Sets](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="7427e-106">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="7427e-106">The WCF Client Class</span></span>  
 <span data-ttu-id="7427e-107">叫用要求設定所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]列於下表。</span><span class="sxs-lookup"><span data-stu-id="7427e-107">The name of the WCF client generated for invoking the request sets by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="7427e-108">成品</span><span class="sxs-lookup"><span data-stu-id="7427e-108">Artifact</span></span>|<span data-ttu-id="7427e-109">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="7427e-109">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="7427e-110">要求組</span><span class="sxs-lookup"><span data-stu-id="7427e-110">Request Set</span></span>|<span data-ttu-id="7427e-111">RequestSets_ [APP_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="7427e-111">RequestSets_[APP_NAME]Client</span></span>|  
  
 <span data-ttu-id="7427e-112">[APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，SQLAP。</span><span class="sxs-lookup"><span data-stu-id="7427e-112">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, SQLAP.</span></span>  
  
### <a name="method-signature-for-invoking-request-sets"></a><span data-ttu-id="7427e-113">叫用要求集的方法簽章</span><span class="sxs-lookup"><span data-stu-id="7427e-113">Method Signature for Invoking Request Sets</span></span>  
 <span data-ttu-id="7427e-114">下表顯示要求的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="7427e-114">The following table shows the method signature for request sets.</span></span>  
  
|<span data-ttu-id="7427e-115">作業</span><span class="sxs-lookup"><span data-stu-id="7427e-115">Operation</span></span>|<span data-ttu-id="7427e-116">方法簽章</span><span class="sxs-lookup"><span data-stu-id="7427e-116">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="7427e-117">要求組</span><span class="sxs-lookup"><span data-stu-id="7427e-117">Request Set</span></span>|<span data-ttu-id="7427e-118">公用\<傳回型別\>\<要求設定名稱\>（參數 1，參數 2，...）</span><span class="sxs-lookup"><span data-stu-id="7427e-118">public \<return type\> \<request set name\>(param 1, param 2, …)</span></span>|  
  
 <span data-ttu-id="7427e-119">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**reqset_singlestage**要求集。</span><span class="sxs-lookup"><span data-stu-id="7427e-119">As an example, the following code shows the method signatures for a WCF client class generated for the **reqset_singlestage** request set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7427e-120">這是自訂要求組，並可能無法使用 Oracle E-business 方案執行個體上。</span><span class="sxs-lookup"><span data-stu-id="7427e-120">This is a custom request set and might not be available on your Oracle E-Business Solution instance.</span></span>  
  
```  
public partial class RequestSets_SQLAPClient : System.ServiceModel.ClientBase<RequestSets_SQLAP>, RequestSets_SQLAP{      
  
    public string REQSTG(  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRelClassOptions SetRelClassOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,   
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,   
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetNlsOptions SetNlsOptions,  
      string StartTime,  
      schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1 set1_set1);  
}  
```  
  
 <span data-ttu-id="7427e-121">在此程式碼片段， **RequestSets_SQLAPClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7427e-121">In this snippet, **RequestSets_SQLAPClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="7427e-122">**REQSTG**是叫用要求集的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="7427e-122">**REQSTG** is the name of the method to invoke the request set.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-request-sets"></a><span data-ttu-id="7427e-123">建立 WCF 用戶端來叫用要求集</span><span class="sxs-lookup"><span data-stu-id="7427e-123">Creating a WCF Client to Invoke Request Sets</span></span>  
 <span data-ttu-id="7427e-124">Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="7427e-124">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="7427e-125">本章節描述如何建立 WCF 用戶端來叫用**reqset_singlestage**要求集。</span><span class="sxs-lookup"><span data-stu-id="7427e-125">This section describes how to create a WCF client to invoke the **reqset_singlestage** request set.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="7427e-126">若要建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="7427e-126">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="7427e-127">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="7427e-127">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="7427e-128">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7427e-128">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="7427e-129">產生 WCF 用戶端類別**reqset_singlestage**要求集。</span><span class="sxs-lookup"><span data-stu-id="7427e-129">Generate the WCF client class for the **reqset_singlestage** request set.</span></span> <span data-ttu-id="7427e-130">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="7427e-130">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7427e-131">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="7427e-131">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="7427e-132">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="7427e-132">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="7427e-133">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="7427e-133">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="7427e-134">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="7427e-134">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    RequestSets_SQLAPClient client = new RequestSets_SQLAPClient(binding, address);  
    ```  
  
     <span data-ttu-id="7427e-135">在此程式碼片段， `RequestSets_SQLAPClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="7427e-135">In this snippet, `RequestSets_SQLAPClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="7427e-136">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7427e-136">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7427e-137">在此片段中，您明確指定的繫結與端點位址的應用程式程式碼中。</span><span class="sxs-lookup"><span data-stu-id="7427e-137">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="7427e-138">您也可以使用這些值從應用程式組態檔 app.config，也是由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7427e-138">You can also use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="7427e-139">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="7427e-139">For more information about the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="7427e-140">設定用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="7427e-140">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="7427e-141">因為您叫用要求集 Oracle E-business Suite 應用程式中的，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="7427e-141">Because you are invoking request sets in an Oracle E-Business Suite application, you must set the application context.</span></span> <span data-ttu-id="7427e-142">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="7427e-142">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="7427e-143">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="7427e-143">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="7427e-144">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="7427e-144">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="7427e-145">叫用**reqset_singlestage**要求集。</span><span class="sxs-lookup"><span data-stu-id="7427e-145">Invoke the **reqset_singlestage** request set.</span></span>  
  
    ```  
    string RequestID;  
  
    schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1 param =  
        new schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1();  
  
    param.INSPARAMPROG = new schemas.microsoft.com.OracleEBS._2008._05.RequestSetConcurrentProgram.SQLAP.REQSTG.set1.SQLAP1.INSPARAMPROG();  
    param.INSPARAMPROG.p_id = "123";  
    param.INSPARAMPROG.p_name = "MyName";  
  
    try  
    {  
        Console.WriteLine("Invoking the reqset_singlestage request set");  
        RequestID = client.REQSTG(null, null, null, null, null, param);  
        Console.WriteLine("The request ID generated for the request set is : " + RequestID);  
        Console.WriteLine("*****************************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;  
    }  
    ```  
  
10. <span data-ttu-id="7427e-146">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="7427e-146">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    ```  
  
11. <span data-ttu-id="7427e-147">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="7427e-147">Build the project and then run it.</span></span> <span data-ttu-id="7427e-148">應用程式會叫用**reqset_singlestage**要求設定，並傳回要求 ID，寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="7427e-148">The application invokes the **reqset_singlestage** request set and returns a request ID, which is written to the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7427e-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="7427e-149">See Also</span></span>  
 [<span data-ttu-id="7427e-150">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="7427e-150">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)