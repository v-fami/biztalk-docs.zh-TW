---
title: "建立 SQL Server 連接 URI |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688e2215-a4d8-4f55-a37c-7d91c3de080f
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f31b6d6919924d3bb4bb1ac6c817c3f3b3d77dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-sql-server-connection-uri"></a><span data-ttu-id="9c017-102">建立 SQL Server 連接 URI</span><span class="sxs-lookup"><span data-stu-id="9c017-102">Create the SQL Server connection URI</span></span>
<span data-ttu-id="9c017-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]連線 URI 包含配接器用來連接到 SQL Server 資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="9c017-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] connection URI contains properties that the adapter uses to establish a connection to the SQL Server database.</span></span> <span data-ttu-id="9c017-104">本主題提供 SQL Server 連接 URI 的相關資訊，並提供其他主題連結，說明如何在不同的程式設計案例中指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="9c017-104">This topic provides information about the SQL Server connection URI, and provides links to other topics that explain how to specify a URI in different programming scenarios.</span></span>  
  
##  <span data-ttu-id="9c017-105"><a name="FailoverPartner"></a>SQL 配接器的連線 URI</span><span class="sxs-lookup"><span data-stu-id="9c017-105"><a name="FailoverPartner"></a> The Connection URI for the SQL Adapter</span></span>  
 <span data-ttu-id="9c017-106">典型的端點位址 URI 在 WCF 中表示為： `scheme://hostinfoparams?query_string`，其中：</span><span class="sxs-lookup"><span data-stu-id="9c017-106">A typical endpoint address URI in WCF is represented as: `scheme://hostinfoparams?query_string`, where:</span></span>  
  
-   <span data-ttu-id="9c017-107">配置是配置名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-107">scheme is the scheme name.</span></span>  
  
-   <span data-ttu-id="9c017-108">hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-108">hostinfoparams is information required to establish the connection to the host; for example, a server name.</span></span>  
  
-   <span data-ttu-id="9c017-109">query_string 是選擇性的問號 （？） 字元分隔的參數名稱 / 值集合。</span><span class="sxs-lookup"><span data-stu-id="9c017-109">query_string is an optional name-value collection of parameters delimited by a question mark (?).</span></span>  
  
 <span data-ttu-id="9c017-110">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c017-110">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] connection URI adheres to this basic format and is implemented as follows:</span></span>  
  
```  
  
mssql://[Server_Name[:Portno]]/[Database_Instance_Name]/[Database_Name]?FailoverPartner=[Partner_Server_Name]&InboundId=[Inbound_ID]  
```  
  
 <span data-ttu-id="9c017-111">其中，`mssql`是 SQL Server 連接 URI 的配置。</span><span class="sxs-lookup"><span data-stu-id="9c017-111">where, `mssql` is the scheme for the SQL Server connection URI.</span></span>  
  
 <span data-ttu-id="9c017-112">下表說明連線 URI 所包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="9c017-112">The following table explains the properties contained in the connection URI.</span></span>  
  
|<span data-ttu-id="9c017-113">連線 URI 屬性</span><span class="sxs-lookup"><span data-stu-id="9c017-113">Connection URI Property</span></span>|<span data-ttu-id="9c017-114">類別目錄</span><span class="sxs-lookup"><span data-stu-id="9c017-114">Category</span></span>|<span data-ttu-id="9c017-115">Description</span><span class="sxs-lookup"><span data-stu-id="9c017-115">Description</span></span>|  
|-----------------------------|--------------|-----------------|  
|<span data-ttu-id="9c017-116">[SERVER_NAME]</span><span class="sxs-lookup"><span data-stu-id="9c017-116">[SERVER_NAME]</span></span>|<span data-ttu-id="9c017-117">hostinfoparams</span><span class="sxs-lookup"><span data-stu-id="9c017-117">hostinfoparams</span></span>|<span data-ttu-id="9c017-118">安裝 SQL Server 的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-118">Name of the server on which SQL Server is installed.</span></span> <span data-ttu-id="9c017-119">如果您未指定值，配接器會假設伺服器名稱為"localhost"，並與本機伺服器上的 SQL Server 資料庫建立連線。</span><span class="sxs-lookup"><span data-stu-id="9c017-119">If you do not specify a value, the adapter assumes the server name as “localhost” and establishes a connection with the SQL Server database on the local server.</span></span>|  
|<span data-ttu-id="9c017-120">[PORTNO]</span><span class="sxs-lookup"><span data-stu-id="9c017-120">[PORTNO]</span></span>|<span data-ttu-id="9c017-121">hostinfoparams</span><span class="sxs-lookup"><span data-stu-id="9c017-121">hostinfoparams</span></span>|<span data-ttu-id="9c017-122">已建立連接的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="9c017-122">The port number where the connection is established.</span></span> <span data-ttu-id="9c017-123">如果您未指定值，配接器會連接到預設連接埠。</span><span class="sxs-lookup"><span data-stu-id="9c017-123">If you do not specify a value, the adapter connects through the default port.</span></span>|  
|<span data-ttu-id="9c017-124">[DATABASE_INSTANCE_NAME]</span><span class="sxs-lookup"><span data-stu-id="9c017-124">[DATABASE_INSTANCE_NAME]</span></span>|<span data-ttu-id="9c017-125">hostinfoparams</span><span class="sxs-lookup"><span data-stu-id="9c017-125">hostinfoparams</span></span>|<span data-ttu-id="9c017-126">若要連接到 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-126">Name of the SQL Server instance to connect to.</span></span> <span data-ttu-id="9c017-127">如果您未指定值，配接器會連接到預設的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c017-127">If you do not specify a value, the adapter connects to the default database instance.</span></span>|  
|<span data-ttu-id="9c017-128">[DATABASE_NAME]</span><span class="sxs-lookup"><span data-stu-id="9c017-128">[DATABASE_NAME]</span></span>|<span data-ttu-id="9c017-129">hostinfoparams</span><span class="sxs-lookup"><span data-stu-id="9c017-129">hostinfoparams</span></span>|<span data-ttu-id="9c017-130">若要連接到資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-130">Name of the database to connect to.</span></span> <span data-ttu-id="9c017-131">如果您未指定值，配接器會連接到預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c017-131">If you do not specify a value, the adapter connects to the default database.</span></span>|  
|<span data-ttu-id="9c017-132">[PARTNER_SERVER_NAME]</span><span class="sxs-lookup"><span data-stu-id="9c017-132">[PARTNER_SERVER_NAME]</span></span>|<span data-ttu-id="9c017-133">query_string</span><span class="sxs-lookup"><span data-stu-id="9c017-133">query_string</span></span>|<span data-ttu-id="9c017-134">無法連線到如果主要 SQL Server 資料庫的容錯移轉 SQL Server 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-134">Name of the failover SQL Server database to connect to if the primary SQL Server database is not available.</span></span> <span data-ttu-id="9c017-135">如需高可用性 SQL Server 」 方面的詳細資訊，請參閱[中 SQL Server 資料庫鏡像](https://msdn.microsoft.com/library/5h52hef8.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9c017-135">For more information about high availability with respect to SQL Server, see [Database Mirroring in SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).</span></span>|  
|<span data-ttu-id="9c017-136">[INBOUND_ID]</span><span class="sxs-lookup"><span data-stu-id="9c017-136">[INBOUND_ID]</span></span>|<span data-ttu-id="9c017-137">query_string</span><span class="sxs-lookup"><span data-stu-id="9c017-137">query_string</span></span>|<span data-ttu-id="9c017-138">您將加入至 URI 成為唯一連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c017-138">An identifier that you add to the connection URI to make it unique.</span></span> <span data-ttu-id="9c017-139">如果您想要產生的中繼資料，您必須提供這個連線參數**TypedPolling**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="9c017-139">You must provide this connection parameter if you want to generate metadata for the **TypedPolling** inbound operation.</span></span> <span data-ttu-id="9c017-140">此外，在 BizTalk 應用程式中，如果您有多個接收位置的輪詢相同的資料庫中，輸入的識別碼建立的連接 URI 唯一的因此會啟用以接收來自不同的相同資料庫輪詢訊息的配接器用戶端接收位置。</span><span class="sxs-lookup"><span data-stu-id="9c017-140">Also, in a BizTalk application, if you have multiple receive locations polling the same database, the inbound ID makes the connection URI unique, thereby enabling adapter clients to receive polling messages from the same database on different receive locations.</span></span> <span data-ttu-id="9c017-141">如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-141">For more information, see [Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9c017-142">如需有關這些連接字串屬性的詳細資訊，請參閱[SqlConnection.ConnectionString 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9c017-142">For more information about these connection string properties, see [SqlConnection.ConnectionString Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx).</span></span>
  
## <a name="sql-server-credentials-and-the-connection-uri"></a><span data-ttu-id="9c017-143">SQL Server 認證和連線 URI</span><span class="sxs-lookup"><span data-stu-id="9c017-143">SQL Server Credentials and the Connection URI</span></span>  
 <span data-ttu-id="9c017-144">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援連線 URI 中指定的認證。</span><span class="sxs-lookup"><span data-stu-id="9c017-144">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support specifying credentials in the connection URI.</span></span> <span data-ttu-id="9c017-145">如需有關在您使用的應用程式中指定認證[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[安全 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-145">For more information about specifying credentials in your applications that use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).</span></span>  
  
## <a name="using-special-characters-in-the-connection-uri"></a><span data-ttu-id="9c017-146">在 連線 URI 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="9c017-146">Using Special Characters in the Connection URI</span></span>  
 <span data-ttu-id="9c017-147">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援指定的連接有任何參數值的特殊字元的 URI。</span><span class="sxs-lookup"><span data-stu-id="9c017-147">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support specifying a connection URI that has special characters for any of the parameter values.</span></span> <span data-ttu-id="9c017-148">如果連線參數值包含特殊字元，請確定您執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9c017-148">If the connection parameter values contain special characters, make sure you do one of the following:</span></span>  
  
-   <span data-ttu-id="9c017-149">如果您要指定中的 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。</span><span class="sxs-lookup"><span data-stu-id="9c017-149">If you are specifying the URI in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters.</span></span> <span data-ttu-id="9c017-150">如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含特殊字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="9c017-150">If you specify the URI directly in the **Configure a URI** field and the connection parameters contain special characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
     <span data-ttu-id="9c017-151">例如，如果連線 URI 的參數名稱與`sql server`，您必須指定它做為`sql%20server`。</span><span class="sxs-lookup"><span data-stu-id="9c017-151">For example, if the connection URI has a parameter with name `sql server`, you must specify it as `sql%20server`.</span></span>  
  
-   <span data-ttu-id="9c017-152">如果您所指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數可以包含特殊字元，您必須指定連接參數使用適當的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="9c017-152">If you are specifying the URI while creating a send or receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and the connection parameters contain special characters, you must specify the connection parameters using proper escape characters.</span></span>  
  
## <a name="using-the-connection-uri-to-connect-to-the-sql-server-database"></a><span data-ttu-id="9c017-153">使用連線到 SQL Server 資料庫的連線 URI</span><span class="sxs-lookup"><span data-stu-id="9c017-153">Using the Connection URI to Connect to the SQL Server Database</span></span>  
 <span data-ttu-id="9c017-154">以下是範例連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9c017-154">The following is a sample connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
```  
mssql://sql_server/sql_server_instance//  
```  
  
 <span data-ttu-id="9c017-155">在上述範例中，「 sql_server 」 是而 」 然後"則是連接到資料庫執行個體的名稱，SQL Server 安裝所在電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c017-155">In the preceding example, “sql_server” is the name of the computer on which SQL Server is installed whereas “sql_server_instance” is the name of the database instance to connect to.</span></span> <span data-ttu-id="9c017-156">因為未指定資料庫名稱時，配接器會連接到預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c017-156">Because no database name is specified, the adapter will connect to the default database.</span></span>  
  
 <span data-ttu-id="9c017-157">下列是連線 URI 的同一部電腦安裝 SQL Server 資料庫的範例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9c017-157">The following is an example of a connection URI where the SQL Server database is installed on the same computer as the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="9c017-158">在此範例中，配接器會連接到資料庫"my_database"」 然後 「 資料庫執行個體，在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="9c017-158">In this example, the adapter connects to the database “my_database” for the “sql_server_instance” database instance on the local computer.</span></span>  
  
```  
mssql://localhost/sql_server_instance/my_database/  
```  
  
 <span data-ttu-id="9c017-159">在此範例中，配接器會連接到本機電腦上執行的預設執行個體的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c017-159">In this example, the adapter connects to the default database for the default instance running on the local computer.</span></span>  
  
```  
mssql://localhost///  
```  
  
 <span data-ttu-id="9c017-160">如需如何指定連接到 SQL Server 資料庫時您：</span><span class="sxs-lookup"><span data-stu-id="9c017-160">For information about how to specify a connection to the SQL Server database when you:</span></span>  
  
-   <span data-ttu-id="9c017-161">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-161">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Connect to SQL Server in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="9c017-162">設定傳送埠或接收埠 （位置） 中的 BizTalk Server 解決方案，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-162">Configure a send port or receive port (location) in a BizTalk Server solution, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span>
  
-   <span data-ttu-id="9c017-163">使用程式設計方案中的 WCF 通道模型，請參閱[建立使用 SQL 配接器的通道](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-163">Use the WCF channel model in a programming solution, see [Create a channel using the SQL adapter](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="9c017-164">使用 WCF 服務模型程式設計方案中，請參閱[設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9c017-164">Use the WCF service model in a programming solution, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c017-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c017-165">See Also</span></span>  
[<span data-ttu-id="9c017-166">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="9c017-166">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)