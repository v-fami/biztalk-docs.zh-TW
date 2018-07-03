---
title: 使用 Oracle E-business Suite 配接器的 WCF 服務模型的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a591c06b89464f640ea4992b927a68a62e69307
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994623"
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="b9b90-102">使用 Oracle E-business Suite 配接器的 WCF 服務模型概觀</span><span class="sxs-lookup"><span data-stu-id="b9b90-102">Overview of the WCF service model with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="b9b90-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開為 WCF 服務的 Oracle E-business Suite 系統。</span><span class="sxs-lookup"><span data-stu-id="b9b90-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes an Oracle E-Business Suite system as a WCF service.</span></span> <span data-ttu-id="b9b90-104">若要執行作業，在 Oracle E-business Suite 的成品，例如若要叫用預存程序中，您叫用的配接器，接著執行 Oracle E-business suite 作業的作業。</span><span class="sxs-lookup"><span data-stu-id="b9b90-104">To perform operations on Oracle E-Business Suite artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the Oracle E-Business Suite.</span></span> <span data-ttu-id="b9b90-105">您的程式碼做為配接器所呈現之 WCF 服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9b90-105">Your code acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="b9b90-106">在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。</span><span class="sxs-lookup"><span data-stu-id="b9b90-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="b9b90-107">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="b9b90-107">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="b9b90-108">這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="b9b90-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="b9b90-109">用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。</span><span class="sxs-lookup"><span data-stu-id="b9b90-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span>  
  
 <span data-ttu-id="b9b90-110">下一節會說明如何使用 WCF 服務模型叫用 WCF 用戶端的作業。</span><span class="sxs-lookup"><span data-stu-id="b9b90-110">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-oracle-e-business-suite-with-a-wcf-client"></a><span data-ttu-id="b9b90-111">針對 Oracle E-business Suite，與 WCF 用戶端叫用作業</span><span class="sxs-lookup"><span data-stu-id="b9b90-111">Invoking Operations on the Oracle E-Business Suite with a WCF Client</span></span>  
 <span data-ttu-id="b9b90-112">若要使用 WCF 服務模型上叫用作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="b9b90-112">To use the WCF service model to invoke operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="b9b90-113">然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業上 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="b9b90-113">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Oracle E-Business Suite.</span></span>  
  
#### <a name="to-invoke-operations-on-the-oracle-e-business-adapter"></a><span data-ttu-id="b9b90-114">若要叫用 Oracle E-business 配接器上的作業</span><span class="sxs-lookup"><span data-stu-id="b9b90-114">To invoke operations on the Oracle E-Business adapter</span></span>  
  
1. <span data-ttu-id="b9b90-115">產生 WCF 用戶端類別和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9b90-115">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="b9b90-116">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 以產生 WCF 用戶端類別作為目標的 Oracle E-business Suite 成品與您想要使用。</span><span class="sxs-lookup"><span data-stu-id="b9b90-116">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at Oracle E-Business Suite artifacts with which you want to work.</span></span> <span data-ttu-id="b9b90-117">如需如何產生 WCF 用戶端的詳細資訊，請參閱[Oracle E-business 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b90-117">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
2. <span data-ttu-id="b9b90-118">建立 WCF 用戶端執行個體並設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9b90-118">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="b9b90-119">設定 WCF 用戶端包含指定的繫結和用戶端會使用的端點位址 （連線 URI）。</span><span class="sxs-lookup"><span data-stu-id="b9b90-119">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="b9b90-120">以命令方式在程式碼或是宣告式組態中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="b9b90-120">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="b9b90-121">下列程式碼會建立 WCF 用戶端為目標**客戶介面**中的並行處理程式**應收帳款**Oracle E-business Suite 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9b90-121">The following code creates a WCF client that targets the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span> <span data-ttu-id="b9b90-122">它也適用於 Oracle E-business Suite 中設定的認證。</span><span class="sxs-lookup"><span data-stu-id="b9b90-122">It also sets the credentials for the Oracle E-Business Suite.</span></span> <span data-ttu-id="b9b90-123">WCF 用戶端會從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="b9b90-123">The WCF client is initialized from configuration.</span></span>  
  
   ```  
   ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
   > [!NOTE]
   >  <span data-ttu-id="b9b90-124">您可以在程式碼中指定的用戶端繫結與端點位址，或宣告中的 app.config 組態檔。</span><span class="sxs-lookup"><span data-stu-id="b9b90-124">You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file.</span></span> <span data-ttu-id="b9b90-125">上面的程式碼片段會使用後者。</span><span class="sxs-lookup"><span data-stu-id="b9b90-125">The preceding code snippet uses the latter.</span></span> <span data-ttu-id="b9b90-126">如需有關如何使用任一種方法的詳細資訊，請參閱 < [for Oracle E-business Suite 中設定 用戶端繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b90-126">For more information on how to use either approaches, see [Configure a Client Binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
3. <span data-ttu-id="b9b90-127">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9b90-127">Open the WCF client.</span></span>  
  
   ```  
   client.Open();  
   ```  
  
4. <span data-ttu-id="b9b90-128">叫用 WCF 用戶端上步驟 2 中建立 Oracle E-business Suite 上執行作業的方法。</span><span class="sxs-lookup"><span data-stu-id="b9b90-128">Invoke methods on the WCF client created in step 2 to perform operations on the Oracle E-Business Suite.</span></span> <span data-ttu-id="b9b90-129">下列程式碼會叫用**客戶介面**中的並行處理程式**應收帳款**Oracle E-business Suite 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9b90-129">The following code invokes the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span>  
  
   ```  
   string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
   ```  
  
    <span data-ttu-id="b9b90-130">**RACUST**是客戶介面並行處理程式的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="b9b90-130">**RACUST** is the actual name of the Customer Interface concurrent program.</span></span> <span data-ttu-id="b9b90-131">**客戶介面**是並行處理程式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b9b90-131">**Customer Interface** is the friendly name of the concurrent program.</span></span>  
  
5. <span data-ttu-id="b9b90-132">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9b90-132">Close the WCF client.</span></span>  
  
   ```  
   client.Close();  
   ```  
  
## <a name="see-also"></a><span data-ttu-id="b9b90-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b90-133">See Also</span></span>  
 [<span data-ttu-id="b9b90-134">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="b9b90-134">Develop Oracle E-Business Suite Applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)