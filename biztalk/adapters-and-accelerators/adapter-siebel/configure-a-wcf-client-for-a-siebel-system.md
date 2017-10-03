---
title: "設定 Siebel 系統的 WCF 用戶端 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, create a WCF client by specifying binding and endpoint address in a configuration file
- how to, create a WCF client by specifying binding and endpoint address in code
- WCF service model, configuring a WCF client for a Siebel system
ms.assetid: 6b4c5b06-d5ff-4dbf-8dc2-89c547a59864
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2395f8698c31a51466cfc98834cec137bf58a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-wcf-client-for-a-siebel-system"></a><span data-ttu-id="9e309-102">設定 Siebel 系統的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="9e309-102">Configure a WCF Client for a Siebel System</span></span>
<span data-ttu-id="9e309-103">產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e309-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="9e309-104">如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約為 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="9e309-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes, see [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="9e309-105">若要建立 WCF 用戶端，您必須指定端點位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="9e309-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="9e309-106">端點位址必須包含有效的 Siebel 連接 URI，且繫結必須 Siebel 繫結執行個體 (**SiebelBinding**)。</span><span class="sxs-lookup"><span data-stu-id="9e309-106">The endpoint address must contain a valid Siebel connection URI, and the binding must be an instance of a Siebel Binding (**SiebelBinding**).</span></span> <span data-ttu-id="9e309-107">如需有關 Siebel 連線 URI 的詳細資訊，請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9e309-107">For more information about the Siebel connection URI, see [Connect to the Siebel System in Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="9e309-108">在您的程式碼或組態檔中，您可以指定 Siebel 繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="9e309-108">You can specify the Siebel Binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="9e309-109">當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。</span><span class="sxs-lookup"><span data-stu-id="9e309-109">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="9e309-110">這個檔案包含組態設定會反映的繫結屬性與連接資訊 （除了認證），您可以指定當您連接至 Siebel 系統具有[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e309-110">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Siebel system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="9e309-111">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="9e309-111">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="9e309-112">下列程式碼會示範如何建立 WCF 用戶端程式碼中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="9e309-112">The following code shows how to create a WCF client by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="9e309-113">使用指定的 Siebel 認證的最佳作法是**ClientCredentials**的 WCF 用戶端，而不是連接的端點位址所提供的 URI 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e309-113">It is good practice to specify the Siebel credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.</span></span>  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by using a binding object and endpoint address  
SiebelBinding sblBinding = new SiebelBinding();  
EndpointAddress sblAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu");  
  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient(sblBinding, sblAddress);  
  
    client.ClientCredentials.UserName.UserName = "SADMIN";  
    client.ClientCredentials.UserName.Password = "SADMIN";  
  
    client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="9e309-114">在組態檔中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="9e309-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="9e309-115">下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="9e309-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by specifying the client endpoint information in app.config  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
client.ClientCredentials.UserName.UserName = "SADMIN";  
client.ClientCredentials.UserName.Password = "SADMIN";  
  
client.Open();  
```  
  
### <a name="the-appconfig-file"></a><span data-ttu-id="9e309-116">App.config 檔案</span><span class="sxs-lookup"><span data-stu-id="9e309-116">The App.config File</span></span>  
 <span data-ttu-id="9e309-117">下列 XML 顯示時間戳記商務服務所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e309-117">The following XML shows the configuration file created for the TimeStamp business service by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="9e309-118">此檔案包含在上述範例中所參考的用戶端端點組態。</span><span class="sxs-lookup"><span data-stu-id="9e309-118">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <siebelBinding>  
                <binding name="SiebelBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    enablePerformanceCounters="false" enableConnectionPooling="true"  
                    maxConnectionsPerSystem="5" idleConnectionTimeout="00:01:00"  
                    acceptCredentialsInUri="false" />  
            </siebelBinding>  
        </bindings>  
        <client>  
            <endpoint address="siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu"  
                binding="siebelBinding" bindingConfiguration="SiebelBinding"  
                contract="BusinessServices_TimeStamp_Operation" name="SiebelBinding_BusinessServices_TimeStamp_Operation" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9e309-119">如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。</span><span class="sxs-lookup"><span data-stu-id="9e309-119">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="9e309-120">每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 Siebel 成品。例如，"SiebelBinding_BusinessServices_TimeStamp_Operation"。</span><span class="sxs-lookup"><span data-stu-id="9e309-120">Each WCF client entry will have a unique name based on its binding configuration and target Siebel artifact; for example, " SiebelBinding_BusinessServices_TimeStamp_Operation ".</span></span> <span data-ttu-id="9e309-121">如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。</span><span class="sxs-lookup"><span data-stu-id="9e309-121">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="9e309-122">這些繫結組態項目將會透過下列方式命名： SiebelBinding、 SiebelBinding1、 SiebelBinding2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="9e309-122">These binding configuration entries will be named in the following manner: SiebelBinding, SiebelBinding1, SiebelBinding2, and so on.</span></span> <span data-ttu-id="9e309-123">在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="9e309-123">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e309-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e309-124">See Also</span></span>  
 [<span data-ttu-id="9e309-125">開發 Siebel 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="9e309-125">Develop Siebel Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)