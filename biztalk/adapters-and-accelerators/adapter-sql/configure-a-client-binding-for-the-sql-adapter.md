---
title: "設定用戶端繫結 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 146e6f51-e33b-45be-a302-8c9250e79501
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af27363e5156ca88f2c6b3e06a67d0609bf52afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-sql-adapter"></a><span data-ttu-id="15c7c-102">設定 SQL 配接器的用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="15c7c-102">Configure a Client Binding for the SQL Adapter</span></span>
<span data-ttu-id="15c7c-103">產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15c7c-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="15c7c-104">如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="15c7c-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
 <span data-ttu-id="15c7c-105">若要建立 WCF 用戶端，您必須指定端點位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="15c7c-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="15c7c-106">端點位址必須包含有效的 SQL 連接 URI，且繫結必須是 SQL 繫結執行個體 (**sqlBinding**)。</span><span class="sxs-lookup"><span data-stu-id="15c7c-106">The endpoint address must contain a valid SQL connection URI, and the binding must be an instance of a SQL Binding (**sqlBinding**).</span></span> <span data-ttu-id="15c7c-107">如需 SQL 連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="15c7c-107">For more information about the SQL connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span> <span data-ttu-id="15c7c-108">您必須指定使用者認證連線 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="15c7c-108">You must specify the user credentials as part of the connection URI.</span></span> <span data-ttu-id="15c7c-109">您可以使用**ClientCredentials** WCF 用戶端，如本主題所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="15c7c-109">You may use the **ClientCredentials** property of the WCF client, as explained in this topic.</span></span>  
  
 <span data-ttu-id="15c7c-110">在您的程式碼或組態檔中，您可以指定 SQL 繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="15c7c-110">You can specify the SQL binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="15c7c-111">當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。</span><span class="sxs-lookup"><span data-stu-id="15c7c-111">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="15c7c-112">這個檔案包含反映的繫結屬性和連接資訊 （除了認證），您可以指定當您連接到 SQL 資料庫的組態設定[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15c7c-112">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the SQL database with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="15c7c-113">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="15c7c-113">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="15c7c-114">下列程式碼示範如何使用程式碼中指定的繫結與端點位址來建立 WCF 用戶端**ClientCredentials** WCF 用戶端的屬性。</span><span class="sxs-lookup"><span data-stu-id="15c7c-114">The following code shows how to create a WCF client by specifying the binding and endpoint address in code by using the **ClientCredentials** property of the WCF client.</span></span>  
  
```  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress sqlAddress = new EndpointAddress("mssql://<sql_server_name>//<database_name>?");  
  
TableOp_dbo_CustomerClient client = new TableOp_dbo_CustomerClient (binding, sqlAddress);  
  
client.ClientCredentials.UserName.UserName = "USER";  
client.ClientCredentials.UserName.Password = "PASSWORD";  
  
client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="15c7c-115">在組態檔中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="15c7c-115">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="15c7c-116">下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="15c7c-116">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
TableOp_dbo_CustomerClient client = new TableOp_dbo_CustomerClient("SqlAdapterBinding_TableOp_dbo_Customer");  
  
client.ClientCredentials.UserName.UserName = "USER";  
client.ClientCredentials.UserName.Password = "PASSWORD";  
  
client.Open();  
```  
  
 <span data-ttu-id="15c7c-117">下列 XML 顯示客戶資料表所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15c7c-117">The following XML shows the configuration file created for the Customer table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="15c7c-118">此檔案包含在上述範例中所參考的用戶端端點組態。</span><span class="sxs-lookup"><span data-stu-id="15c7c-118">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <sqlBinding>  
                <binding name="SqlAdapterBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" maxConnectionPoolSize="100"  
                    encrypt="false" useAmbientTransaction="true" batchSize="20"  
                    polledDataAvailableStatement="" pollingStatement="" pollingIntervalInSeconds="30"  
                    pollWhileDataFound="false" notificationStatement="" notifyOnListenerStart="true"  
                    enableBizTalkCompatibilityMode="true" chunkSize="4194304"  
                    inboundOperationType="Polling" useDatabaseNameInXsdNamespace="false"  
                    allowIdentityInsert="false" enablePerformanceCounters="false"  
                    xmlStoredProcedureRootNodeName="" xmlStoredProcedureRootNodeNamespace="" />  
            </sqlBinding>  
        </bindings>  
        <client>  
            <endpoint address="mssql://<sql_server_name>//<database_name>?" binding="sqlBinding"  
                bindingConfiguration="SqlAdapterBinding" contract="TableOp_dbo_Customer"  
                name="SqlAdapterBinding_TableOp_dbo_Customer" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="15c7c-119">如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。</span><span class="sxs-lookup"><span data-stu-id="15c7c-119">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="15c7c-120">每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 SQL Server 成品。例如，"`SqlAdapterBinding_TableOp_dbo_Customer`"。</span><span class="sxs-lookup"><span data-stu-id="15c7c-120">Each WCF client entry will have a unique name based on its binding configuration and target SQL Server artifact; for example, "`SqlAdapterBinding_TableOp_dbo_Customer`".</span></span> <span data-ttu-id="15c7c-121">如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。</span><span class="sxs-lookup"><span data-stu-id="15c7c-121">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="15c7c-122">這些繫結組態項目將會透過下列方式命名： SqlAdapterBinding、 SqlAdapterBinding1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="15c7c-122">These binding configuration entries will be named in the following manner: SqlAdapterBinding, SqlAdapterBinding1, and so on.</span></span> <span data-ttu-id="15c7c-123">在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="15c7c-123">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c7c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15c7c-124">See Also</span></span>  
<span data-ttu-id="15c7c-125">[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="15c7c-125">[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md) </span></span>  
 <span data-ttu-id="15c7c-126">[SQL Server 成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md) </span><span class="sxs-lookup"><span data-stu-id="15c7c-126">[Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md) </span></span>  
[<span data-ttu-id="15c7c-127">建立 SQL Server 連接 URI</span><span class="sxs-lookup"><span data-stu-id="15c7c-127">Create the SQL Server connection URI</span></span>](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)