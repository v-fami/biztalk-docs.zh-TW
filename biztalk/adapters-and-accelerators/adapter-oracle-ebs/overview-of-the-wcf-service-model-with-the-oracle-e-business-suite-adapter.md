---
title: "Oracle E-business Suite 配接器之 WCF 服務模型的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40b22865ca45cbd10823f6c514f75e5965f1df5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="fa6d9-102">Oracle E-business Suite 配接器的 WCF 服務模型概觀</span><span class="sxs-lookup"><span data-stu-id="fa6d9-102">Overview of the WCF service model with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="fa6d9-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開為 WCF 服務的 Oracle E-business Suite 系統。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes an Oracle E-Business Suite system as a WCF service.</span></span> <span data-ttu-id="fa6d9-104">對 Oracle E-business Suite 成品，例如若要叫用預存程序中，執行作業您叫用的配接器，接著執行 Oracle E-business suite 作業的作業。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-104">To perform operations on Oracle E-Business Suite artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the Oracle E-Business Suite.</span></span> <span data-ttu-id="fa6d9-105">您的程式碼做為配接器所呈現之 WCF 服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-105">Your code acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="fa6d9-106">在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="fa6d9-107">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-107">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="fa6d9-108">這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="fa6d9-109">用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span>  
  
 <span data-ttu-id="fa6d9-110">下節說明如何使用 WCF 服務模型來叫用的 WCF 用戶端的作業。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-110">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-oracle-e-business-suite-with-a-wcf-client"></a><span data-ttu-id="fa6d9-111">叫用 Oracle E-business Suite，與 WCF 用戶端上的作業</span><span class="sxs-lookup"><span data-stu-id="fa6d9-111">Invoking Operations on the Oracle E-Business Suite with a WCF Client</span></span>  
 <span data-ttu-id="fa6d9-112">若要使用 WCF 服務模型上叫用作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-112">To use the WCF service model to invoke operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="fa6d9-113">然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業 Oracle E-business suite。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-113">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Oracle E-Business Suite.</span></span>  
  
#### <a name="to-invoke-operations-on-the-oracle-e-business-adapter"></a><span data-ttu-id="fa6d9-114">要叫用 Oracle E-business 配接器的作業</span><span class="sxs-lookup"><span data-stu-id="fa6d9-114">To invoke operations on the Oracle E-Business adapter</span></span>  
  
1.  <span data-ttu-id="fa6d9-115">產生 WCF 用戶端類別和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-115">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="fa6d9-116">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標的 Oracle E-business Suite 成品想要使用。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-116">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at Oracle E-Business Suite artifacts with which you want to work.</span></span> <span data-ttu-id="fa6d9-117">如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-117">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="fa6d9-118">建立 WCF 用戶端執行個體並設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-118">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="fa6d9-119">設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址 （連線 URI）。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-119">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="fa6d9-120">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-120">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="fa6d9-121">下列程式碼會建立 WCF 用戶端為目標**客戶介面**中的並行程式**應收帳款**Oracle E-business Suite 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-121">The following code creates a WCF client that targets the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span> <span data-ttu-id="fa6d9-122">它也 for Oracle E-business Suite 中設定的認證。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-122">It also sets the credentials for the Oracle E-Business Suite.</span></span> <span data-ttu-id="fa6d9-123">WCF 用戶端會從設定初始化。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-123">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="fa6d9-124">您可以在程式碼中指定的用戶端繫結與端點位址，或宣告 app.config 組態檔中。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-124">You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file.</span></span> <span data-ttu-id="fa6d9-125">上述程式碼片段會使用後者。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-125">The preceding code snippet uses the latter.</span></span> <span data-ttu-id="fa6d9-126">如需有關如何使用任一種方法的詳細資訊，請參閱[for Oracle E-business Suite 中設定 用戶端繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-126">For more information on how to use either approaches, see [Configure a Client Binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
3.  <span data-ttu-id="fa6d9-127">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-127">Open the WCF client.</span></span>  
  
    ```  
    client.Open();  
    ```  
  
4.  <span data-ttu-id="fa6d9-128">叫用 WCF 用戶端上步驟 2 中建立執行 Oracle E-business suite 作業的方法。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-128">Invoke methods on the WCF client created in step 2 to perform operations on the Oracle E-Business Suite.</span></span> <span data-ttu-id="fa6d9-129">下列程式碼會叫用**客戶介面**中的並行程式**應收帳款**Oracle E-business Suite 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-129">The following code invokes the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span>  
  
    ```  
    string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
    ```  
  
     <span data-ttu-id="fa6d9-130">**RACUST**是客戶介面並行程式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-130">**RACUST** is the actual name of the Customer Interface concurrent program.</span></span> <span data-ttu-id="fa6d9-131">**客戶介面**是並行程式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-131">**Customer Interface** is the friendly name of the concurrent program.</span></span>  
  
5.  <span data-ttu-id="fa6d9-132">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="fa6d9-132">Close the WCF client.</span></span>  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa6d9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa6d9-133">See Also</span></span>  
 [<span data-ttu-id="fa6d9-134">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="fa6d9-134">Develop Oracle E-Business Suite Applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)