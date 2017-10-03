---
title: "設定用戶端繫結為 SAP 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxy programming, creating a proxy
- creating a proxy
- how to, create a proxy
ms.assetid: bceef132-29ff-4207-a37d-bf94fab484dd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f75253251d18049363255f553ded833748e33875
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-sap-system"></a><span data-ttu-id="d1b30-102">設定用戶端繫結為 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="d1b30-102">Configure a client binding for the SAP system</span></span>
<span data-ttu-id="d1b30-103">產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1b30-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span> <span data-ttu-id="d1b30-104">如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b30-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="d1b30-105">若要建立 WCF 用戶端，您必須指定端點位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="d1b30-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="d1b30-106">端點位址必須包含有效的 SAP 連接 URI，而且繫結必須是 SAP 繫結執行個體 (**SAPBinding**)。</span><span class="sxs-lookup"><span data-stu-id="d1b30-106">The endpoint address must contain a valid SAP connection URI, and the binding must be an instance of an SAP Binding (**SAPBinding**).</span></span> <span data-ttu-id="d1b30-107">如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b30-107">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
 <span data-ttu-id="d1b30-108">在您的程式碼或組態檔中，您可以指定 SAP 繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="d1b30-108">You can specify the SAP Binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="d1b30-109">當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。</span><span class="sxs-lookup"><span data-stu-id="d1b30-109">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="d1b30-110">這個檔案包含反映的繫結屬性和連接資訊 （除了認證），當您連接至 SAP 系統時，您所指定的組態設定[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1b30-110">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the SAP system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="d1b30-111">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="d1b30-111">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="d1b30-112">下列程式碼會示範如何建立 WCF 用戶端程式碼中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="d1b30-112">The following code shows how to create a WCF client by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="d1b30-113">使用指定的 SAP 系統認證的最佳作法是**ClientCredentials**的 WCF 用戶端，而不是連接的端點位址所提供的 URI 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d1b30-113">It is good practice to specify the SAP system credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.</span></span>  
  
```  
// A WCF client that targets an RFC is created  
// by using a binding object and endpoint address  
SAPBinding sapBinding = new SAPBinding();  
EndpointAddress sapAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00");  
  
RfcClient rfcClient = new RfcClient(sapBinding, sapAddress);  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="d1b30-114">在組態檔中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="d1b30-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="d1b30-115">下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="d1b30-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
// A WCF client that targets an RFC is created  
// by specifying the client endpoint information in app.config  
RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
 <span data-ttu-id="d1b30-116">下列 XML 顯示為 EMP 資料表所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1b30-116">The following XML shows the configuration file created for the EMP table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="d1b30-117">此檔案包含在上述範例中所參考的用戶端端點組態。</span><span class="sxs-lookup"><span data-stu-id="d1b30-117">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" receiveIdocFormat="Typed"  
                    generateFlatFileCompatibleIdocSchema="true" maxConnectionsPerSystem="50"  
                    enableConnectionPooling="true" idleConnectionTimeout="00:15:00"  
                    flatFileSegmentIndicator="SegmentDefinition" enablePerformanceCounters="false"  
                    autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false" padReceivedIdocWithSpaces="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="Rfc"  
                name="SAPBinding_Rfc" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d1b30-118">如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。</span><span class="sxs-lookup"><span data-stu-id="d1b30-118">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="d1b30-119">每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 SAP 系統成品 （例如 Rfc 和 Trfc）;例如，"SAPBinding_Rfc"。</span><span class="sxs-lookup"><span data-stu-id="d1b30-119">Each WCF client entry will have a unique name based on its binding configuration and target SAP system artifacts (such as Rfc and Trfc); for example, "SAPBinding_Rfc".</span></span> <span data-ttu-id="d1b30-120">如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。</span><span class="sxs-lookup"><span data-stu-id="d1b30-120">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="d1b30-121">這些繫結組態項目將會透過下列方式命名： SAPBinding1、 SAPBinding2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d1b30-121">These binding configuration entries will be named in the following manner: SAPBinding1, SAPBinding2, and so on.</span></span> <span data-ttu-id="d1b30-122">在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="d1b30-122">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1b30-123">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現不同 SAP 成品 （例如 RFC、 TRFC 和 IDOC） 相同的類型做為相同的服務合約的不同作業。</span><span class="sxs-lookup"><span data-stu-id="d1b30-123">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces different SAP artifacts of the same type (such as RFC, TRFC, and IDOC) as different operations of the same service contract.</span></span> <span data-ttu-id="d1b30-124">例如，兩個不同的 Rfc、 RFC_EXAMPLE_A 和 RFC_EXAMPLE_B，會同時發生在相同的服務合約 (「 Rfc")。</span><span class="sxs-lookup"><span data-stu-id="d1b30-124">For example, two different RFCs, RFC_EXAMPLE_A and RFC_EXAMPLE_B, will both be surfaced under the same service contract ("Rfc").</span></span> <span data-ttu-id="d1b30-125">這表示會在相同的 WCF 用戶端類別，所叫用這兩個 Rfc **RfcClient**，而且這兩個 Rfc 的參數會在相同的命名空間中宣告。</span><span class="sxs-lookup"><span data-stu-id="d1b30-125">This means that both RFCs will be invoked by the same WCF client class, **RfcClient**, and that the parameters for both RFCs will be declared in the same namespace.</span></span> <span data-ttu-id="d1b30-126">因此，您必須在相同產生 WCF 用戶端，這兩個 rfc[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]以避免當您建置方案時遇到的命名空間衝突的工作階段 （連線）。</span><span class="sxs-lookup"><span data-stu-id="d1b30-126">Therefore, you must generate the WCF client for both RFCs during the same [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] session (connection) to avoid experiencing a namespace collision when you build your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b30-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1b30-127">See Also</span></span>  
<span data-ttu-id="d1b30-128">[開發使用 WCF 服務模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="d1b30-128">[Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 <span data-ttu-id="d1b30-129">[產生 WCF 用戶端或 SAP 方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md) </span><span class="sxs-lookup"><span data-stu-id="d1b30-129">[Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md) </span></span>  
 [<span data-ttu-id="d1b30-130">建立 SAP 系統連線 URI</span><span class="sxs-lookup"><span data-stu-id="d1b30-130">Create the SAP system connection URI</span></span>](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)