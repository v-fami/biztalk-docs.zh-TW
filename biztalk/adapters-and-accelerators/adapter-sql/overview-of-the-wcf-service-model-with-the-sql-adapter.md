---
title: "SQL 配接器的 WCF 服務模型的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7641bcc7-3845-4914-9b1b-cb86b998ea6d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3afbf1822945f0a47b09a93b3ac3cc2f8ac8653d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-sql-adapter"></a><span data-ttu-id="e2c4f-102">SQL 配接器的 WCF 服務模型概觀</span><span class="sxs-lookup"><span data-stu-id="e2c4f-102">Overview of the WCF service model with the SQL adapter</span></span>
<span data-ttu-id="e2c4f-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 作業。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes a SQL Server operation as a WCF service.</span></span> <span data-ttu-id="e2c4f-104">若要執行作業，SQL Server 成品，例如若要叫用預存程序，在您叫用的配接器，接著執行 SQL Server 上的作業上的作業。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-104">To perform operations on SQL Server artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the SQL Server.</span></span> <span data-ttu-id="e2c4f-105">您的程式碼因此可做為配接器所呈現之 WCF 服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-105">Your code therefore acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="e2c4f-106">在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="e2c4f-107">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-107">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="e2c4f-108">這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="e2c4f-109">用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span> <span data-ttu-id="e2c4f-110">若要實作服務以接收來自輸入的操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，實作的輸入作業所產生的介面。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-110">To implement a service to receive inbound operations from the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you implement the interface generated for the inbound operations.</span></span>  
  
 <span data-ttu-id="e2c4f-111">下節說明如何使用 WCF 服務模型來叫用的 WCF 用戶端的作業。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-111">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-sql-server-with-a-wcf-client"></a><span data-ttu-id="e2c4f-112">SQL Server 的 WCF 用戶端上叫用作業</span><span class="sxs-lookup"><span data-stu-id="e2c4f-112">Invoking Operations on the SQL Server with a WCF Client</span></span>  
 <span data-ttu-id="e2c4f-113">若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-113">To use the WCF service model to invoke operations on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="e2c4f-114">然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業的 SQL Server 系統上。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-114">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the SQL Server system.</span></span> <span data-ttu-id="e2c4f-115">本章節提供一般的.NET 配接器用戶端應用程式看起來像外的框。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-115">This section provides an outline of how a typical .NET adapter client application looks like.</span></span> <span data-ttu-id="e2c4f-116">特定的主題會提供有關如何執行不同的作業上使用配接器的 SQL Server 資料庫的詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-116">Detailed explanations on how to perform different operations on the SQL Server database using the adapter are provided in specific topics.</span></span>  
  
#### <a name="to-invoke-operations-on-the-sql-adapter"></a><span data-ttu-id="e2c4f-117">叫用 SQL 配接器的作業</span><span class="sxs-lookup"><span data-stu-id="e2c4f-117">To invoke operations on the SQL adapter</span></span>  
  
1.  <span data-ttu-id="e2c4f-118">產生 WCF 用戶端類別和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-118">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="e2c4f-119">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別針對您要使用的 SQL Server 資料庫成品。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-119">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]to generate a WCF client class targeted at the SQL Server database artifacts with which you want to work.</span></span> <span data-ttu-id="e2c4f-120">如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-120">For more information about how to generate a WCF client, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="e2c4f-121">建立 WCF 用戶端執行個體並設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-121">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="e2c4f-122">設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址 （連線 URI）。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-122">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="e2c4f-123">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-123">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="e2c4f-124">下列程式碼會建立 WCF 用戶端為目標**選取**作業**員工**SQL Server 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-124">The following code creates a WCF client that targets the **Select** operation on the **Employee** table in a SQL Server database.</span></span> <span data-ttu-id="e2c4f-125">它也會設定 SQL Server 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-125">It also sets the credentials for the SQL Server database.</span></span> <span data-ttu-id="e2c4f-126">WCF 用戶端會從設定初始化。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-126">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee"); //picking the binding and address from the app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e2c4f-127">您可以在程式碼中指定的用戶端繫結與端點位址，或宣告 app.config 組態檔中。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-127">You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file.</span></span> <span data-ttu-id="e2c4f-128">上述程式碼片段會使用後者。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-128">The preceding code snippet uses the latter.</span></span> <span data-ttu-id="e2c4f-129">如需有關如何使用任一種方法的詳細資訊，請參閱[設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-129">For more information on how to use either approaches, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
3.  <span data-ttu-id="e2c4f-130">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-130">Open the WCF client.</span></span>  
  
    ```  
    client.Open();  
    ```  
  
4.  <span data-ttu-id="e2c4f-131">叫用 WCF 用戶端上一個步驟中建立執行 SQL server 資料庫上的選取作業的方法。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-131">Invoke methods on the WCF client created in preceding step to perform a Select operation on the SQL server database.</span></span> <span data-ttu-id="e2c4f-132">下列程式碼會叫用 Select 方法的 WCF 用戶端來叫用的 SQL Server 資料庫資料表上的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-132">The following code invokes the Select method of the WCF client to invoke the SELECT statement on a SQL Server database table.</span></span>  
  
    ```  
    client.Select("*", "where [Name] = ‘John Smith’");  
    ```  
  
5.  <span data-ttu-id="e2c4f-133">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2c4f-133">Close the WCF client.</span></span>  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e2c4f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2c4f-134">See Also</span></span>  
[<span data-ttu-id="e2c4f-135">開發 SQL 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="e2c4f-135">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)