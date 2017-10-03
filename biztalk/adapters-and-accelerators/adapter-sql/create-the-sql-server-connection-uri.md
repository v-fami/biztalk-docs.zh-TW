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
# <a name="create-the-sql-server-connection-uri"></a>建立 SQL Server 連接 URI
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]連線 URI 包含配接器用來連接到 SQL Server 資料庫的屬性。 本主題提供 SQL Server 連接 URI 的相關資訊，並提供其他主題連結，說明如何在不同的程式設計案例中指定的 URI。  
  
##  <a name="FailoverPartner"></a>SQL 配接器的連線 URI  
 典型的端點位址 URI 在 WCF 中表示為： `scheme://hostinfoparams?query_string`，其中：  
  
-   配置是配置名稱。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱。  
  
-   query_string 是選擇性的問號 （？） 字元分隔的參數名稱 / 值集合。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：  
  
```  
  
mssql://[Server_Name[:Portno]]/[Database_Instance_Name]/[Database_Name]?FailoverPartner=[Partner_Server_Name]&InboundId=[Inbound_ID]  
```  
  
 其中，`mssql`是 SQL Server 連接 URI 的配置。  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|Description|  
|-----------------------------|--------------|-----------------|  
|[SERVER_NAME]|hostinfoparams|安裝 SQL Server 的伺服器名稱。 如果您未指定值，配接器會假設伺服器名稱為"localhost"，並與本機伺服器上的 SQL Server 資料庫建立連線。|  
|[PORTNO]|hostinfoparams|已建立連接的連接埠號碼。 如果您未指定值，配接器會連接到預設連接埠。|  
|[DATABASE_INSTANCE_NAME]|hostinfoparams|若要連接到 SQL Server 執行個體的名稱。 如果您未指定值，配接器會連接到預設的資料庫執行個體。|  
|[DATABASE_NAME]|hostinfoparams|若要連接到資料庫的名稱。 如果您未指定值，配接器會連接到預設資料庫。|  
|[PARTNER_SERVER_NAME]|query_string|無法連線到如果主要 SQL Server 資料庫的容錯移轉 SQL Server 資料庫名稱。 如需高可用性 SQL Server 」 方面的詳細資訊，請參閱[中 SQL Server 資料庫鏡像](https://msdn.microsoft.com/library/5h52hef8.aspx)。|  
|[INBOUND_ID]|query_string|您將加入至 URI 成為唯一連接識別碼。 如果您想要產生的中繼資料，您必須提供這個連線參數**TypedPolling**輸入作業。 此外，在 BizTalk 應用程式中，如果您有多個接收位置的輪詢相同的資料庫中，輸入的識別碼建立的連接 URI 唯一的因此會啟用以接收來自不同的相同資料庫輪詢訊息的配接器用戶端接收位置。 如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。|  
  
> [!NOTE]
>  如需有關這些連接字串屬性的詳細資訊，請參閱[SqlConnection.ConnectionString 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx)。
  
## <a name="sql-server-credentials-and-the-connection-uri"></a>SQL Server 認證和連線 URI  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援連線 URI 中指定的認證。 如需有關在您使用的應用程式中指定認證[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[安全 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。  
  
## <a name="using-special-characters-in-the-connection-uri"></a>在 連線 URI 中使用特殊字元  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援指定的連接有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  
  
-   如果您要指定中的 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含特殊字元，您必須指定連接參數使用適當的逸出字元。  
  
     例如，如果連線 URI 的參數名稱與`sql server`，您必須指定它做為`sql%20server`。  
  
-   如果您所指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數可以包含特殊字元，您必須指定連接參數使用適當的逸出字元。  
  
## <a name="using-the-connection-uri-to-connect-to-the-sql-server-database"></a>使用連線到 SQL Server 資料庫的連線 URI  
 以下是範例連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
```  
mssql://sql_server/sql_server_instance//  
```  
  
 在上述範例中，「 sql_server 」 是而 」 然後"則是連接到資料庫執行個體的名稱，SQL Server 安裝所在電腦的名稱。 因為未指定資料庫名稱時，配接器會連接到預設資料庫。  
  
 下列是連線 URI 的同一部電腦安裝 SQL Server 資料庫的範例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 在此範例中，配接器會連接到資料庫"my_database"」 然後 「 資料庫執行個體，在本機電腦上。  
  
```  
mssql://localhost/sql_server_instance/my_database/  
```  
  
 在此範例中，配接器會連接到本機電腦上執行的預設執行個體的預設資料庫。  
  
```  
mssql://localhost///  
```  
  
 如需如何指定連接到 SQL Server 資料庫時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。  
  
-   設定傳送埠或接收埠 （位置） 中的 BizTalk Server 解決方案，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立使用 SQL 配接器的通道](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)