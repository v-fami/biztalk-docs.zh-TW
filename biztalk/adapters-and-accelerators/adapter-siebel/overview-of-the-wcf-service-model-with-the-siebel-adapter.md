---
title: Siebel 配接器之 WCF 服務模型的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, invoke operations on the Siebel system with a WCF client
- WCF service model, overview of
ms.assetid: 0e812473-0f50-4972-8b07-ec8edc2ef000
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c638255b103a9c588f22d6ddcb2a75b81619b73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222110"
---
# <a name="overview-of-the-wcf-service-model-with-the-siebel-adapter"></a><span data-ttu-id="2c372-102">Siebel 配接器之 WCF 服務模型的概觀</span><span class="sxs-lookup"><span data-stu-id="2c372-102">Overview of the WCF service model with the Siebel adapter</span></span>
<span data-ttu-id="2c372-103">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開為 WCF 服務的 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="2c372-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes a Siebel system as a WCF service.</span></span> <span data-ttu-id="2c372-104">在 Siebel 系統成品，例如若要叫用方法的 Siebel 商務服務上執行作業您叫用的配接器，接著執行 Siebel 系統上的作業上的作業。</span><span class="sxs-lookup"><span data-stu-id="2c372-104">To perform operations on Siebel system artifacts, for example to invoke a method of a Siebel business service, you invoke an operation on the adapter, which, in turn, performs the operation on the Siebel system.</span></span> <span data-ttu-id="2c372-105">您的程式碼因此可做為配接器所呈現之 WCF 服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="2c372-105">Your code therefore acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="2c372-106">在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。</span><span class="sxs-lookup"><span data-stu-id="2c372-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="2c372-107">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="2c372-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="2c372-108">這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。</span><span class="sxs-lookup"><span data-stu-id="2c372-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="2c372-109">用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。</span><span class="sxs-lookup"><span data-stu-id="2c372-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span>  
  
 <span data-ttu-id="2c372-110">下節說明如何使用 WCF 服務模型來叫用的 WCF 用戶端的作業。</span><span class="sxs-lookup"><span data-stu-id="2c372-110">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-siebel-system-with-a-wcf-client"></a><span data-ttu-id="2c372-111">叫用 WCF 用戶端在 Siebel 系統的作業</span><span class="sxs-lookup"><span data-stu-id="2c372-111">Invoking Operations on the Siebel System with a WCF Client</span></span>  
 <span data-ttu-id="2c372-112">若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="2c372-112">To use the WCF service model to invoke operations on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="2c372-113">然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來 Siebel 系統上執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="2c372-113">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Siebel system.</span></span>  
  
#### <a name="to-invoke-operations-on-the-siebel-adapter"></a><span data-ttu-id="2c372-114">若要在 Siebel 介面卡上叫用作業</span><span class="sxs-lookup"><span data-stu-id="2c372-114">To invoke operations on the Siebel adapter</span></span>  
  
1.  <span data-ttu-id="2c372-115">產生 WCF 用戶端類別和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="2c372-115">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="2c372-116">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標的 Siebel 系統成品想要使用。</span><span class="sxs-lookup"><span data-stu-id="2c372-116">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the Siebel system artifacts with which you want to work.</span></span> <span data-ttu-id="2c372-117">如需如何產生 WCF 用戶端的詳細資訊，請參閱[Siebel 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="2c372-117">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF service contract for Siebel Solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="2c372-118">建立 WCF 用戶端執行個體並設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2c372-118">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="2c372-119">設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址 （連線 URI）。</span><span class="sxs-lookup"><span data-stu-id="2c372-119">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="2c372-120">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="2c372-120">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="2c372-121">如需如何設定 WCF 用戶端的詳細資訊，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2c372-121">For more information about how to configure the WCF client, see [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).</span></span> <span data-ttu-id="2c372-122">下列程式碼會建立 WCF 用戶端為目標的時間戳記 Siebel 商務服務。</span><span class="sxs-lookup"><span data-stu-id="2c372-122">The following code creates a WCF client that targets the Siebel TimeStamp business service.</span></span> <span data-ttu-id="2c372-123">它也會設定 Siebel 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="2c372-123">It also sets the credentials for the Siebel system.</span></span> <span data-ttu-id="2c372-124">WCF 用戶端會從設定初始化。</span><span class="sxs-lookup"><span data-stu-id="2c372-124">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    BusinessServices_TimeStamp_OperationClient client =  
        new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
    client.ClientCredentials.UserName.UserName = "YourUserName";  
    client.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="2c372-125">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2c372-125">Open the WCF client.</span></span>  
  
    ```  
    client.Open();  
    ```  
  
4.  <span data-ttu-id="2c372-126">叫用 WCF 用戶端上步驟 2 中建立 Siebel 系統上執行作業的方法。</span><span class="sxs-lookup"><span data-stu-id="2c372-126">Invoke methods on the WCF client created in step 2 to perform operations on the Siebel system.</span></span> <span data-ttu-id="2c372-127">下列程式碼會叫用**Execute**方法叫用的 WCF 用戶端**Execute** Siebel 系統上的時間戳記商務服務的方法。</span><span class="sxs-lookup"><span data-stu-id="2c372-127">The following code invokes the **Execute** method of the WCF client to invoke the **Execute** method of the TimeStamp business service on the Siebel system.</span></span>  
  
    ```  
    // Create a parameter to hold the results and then invoke the Execute method of the TimeStamp business service.  
    microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp.ExecuteResponseRecord er;  
    er = client.Execute();  
    ```  
  
5.  <span data-ttu-id="2c372-128">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2c372-128">Close the WCF client.</span></span>  
  
    ```  
    client.Close();  
    ```  
  
 <span data-ttu-id="2c372-129">如需叫用 Siebel 商務服務方法的詳細資訊，請參閱[叫用商務服務方法使用 Siebel 配接器使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)</span><span class="sxs-lookup"><span data-stu-id="2c372-129">For more information about invoking Siebel business service methods, see [Invoke Business Service Methods with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="2c372-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c372-130">See Also</span></span>  
 [<span data-ttu-id="2c372-131">開發 Siebel 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="2c372-131">Develop Siebel Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)