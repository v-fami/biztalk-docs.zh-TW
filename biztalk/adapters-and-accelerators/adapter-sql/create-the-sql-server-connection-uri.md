---
title: 建立 SQL Server 連接 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 688e2215-a4d8-4f55-a37c-7d91c3de080f
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c58812b9fc3404b9922cf05c84717f3c95e05435
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007575"
---
# <a name="create-the-sql-server-connection-uri"></a>建立 SQL Server 連接 URI
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]連線 URI 包含配接器用來連接到 SQL Server 資料庫的屬性。 本主題提供 SQL Server 連接 URI 的相關資訊，並提供其他主題連結，說明如何在不同的程式設計案例中指定的 URI。  
  
##  <a name="FailoverPartner"></a> SQL 配接器的連線 URI  
 典型的端點位址 URI，在 WCF 中表示為： `scheme://hostinfoparams?query_string`，其中：  
  
- 配置為配置名稱。  
  
- hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱。  
  
- query_string 是以問號 （？） 分隔的參數的選擇性名稱 / 值集合。  
  
  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]連線 URI 遵循這個基本的格式，並實作如下：  
  
```  
  
mssql://[Server_Name[:Portno]]/[Database_Instance_Name]/[Database_Name]?FailoverPartner=[Partner_Server_Name]&InboundId=[Inbound_ID]  
```  
  
 其中，`mssql`是 SQL Server 連接 URI 的配置。  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|描述|  
|-----------------------------|--------------|-----------------|  
|[SERVER_NAME]|hostinfoparams|SQL Server 安裝所在的伺服器名稱。 如果您未指定值，配接器會假設為"localhost"的伺服器名稱，並建立與本機伺服器上的 SQL Server 資料庫的連線。|  
|[PORTNO]|hostinfoparams|會建立連接的連接埠號碼。 如果您未指定值，配接器會連接到預設連接埠。|  
|[DATABASE_INSTANCE_NAME]|hostinfoparams|若要連接到 SQL Server 執行個體的名稱。 如果您未指定值，配接器會連接到預設資料庫執行個體。|  
|[DATABASE_NAME]|hostinfoparams|若要連接到資料庫的名稱。 如果您未指定值，配接器會連接到預設資料庫。|  
|[PARTNER_SERVER_NAME]|query_string|無法使用的連接，如果主要的 SQL Server 資料庫的容錯移轉 SQL Server 資料庫的名稱。 如需有關 SQL Server 對於高可用性的詳細資訊，請參閱[SQL Server 中的資料庫鏡像](https://msdn.microsoft.com/library/5h52hef8.aspx)。|  
|[INBOUND_ID]|query_string|您將新增至連線，使它成為唯一的 URI 識別碼。 如果您想要產生的中繼資料，您必須提供這個連接參數**TypedPolling**輸入作業。 此外，在 BizTalk 應用程式中，如果您有多個接收位置輪詢相同的資料庫中，輸入的識別碼建立的連接 URI 唯一的因此會啟用以接收來自不同的相同資料庫輪詢訊息的配接器用戶端接收位置。 如需詳細資訊，請參閱 <<c0> [ 接收輪詢訊息跨多個接收埠從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。|  
  
> [!NOTE]
>  如需有關這些連接字串屬性的詳細資訊，請參閱 < [SqlConnection.ConnectionString 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx)。
  
## <a name="sql-server-credentials-and-the-connection-uri"></a>SQL Server 認證和連線 URI  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援的連線 URI 中指定的認證。 如需有關在您使用的應用程式中指定認證[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 保護您的 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。  
  
## <a name="using-special-characters-in-the-connection-uri"></a>在 連線 URI 中使用特殊字元  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  
  
- 如果您要指定在 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定直接在 URI**設定 URI**欄位和連接參數包含特殊字元，您必須指定下列連線參數，使用適當的逸出字元。  
  
   例如，如果連線 URI 具有名稱的參數`sql server`，您必須指定它當作`sql%20server`。  
  
- 如果您指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數包含特殊字元，您必須指定下列連線參數，使用適當的逸出字元。  
  
## <a name="using-the-connection-uri-to-connect-to-the-sql-server-database"></a>若要連接到 SQL Server 資料庫使用的連線 URI  
 以下是範例連線 URI 的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
```  
mssql://sql_server/sql_server_instance//  
```  
  
 在上述範例中，「 sql_server"會是而 「 然後 」 則是連線到資料庫執行個體的名稱，SQL Server 安裝所在電腦的名稱。 因為未不指定任何資料庫名稱的介面卡會連線到預設資料庫。  
  
 以下是連線 URI 的同一部電腦安裝 SQL Server 資料庫的範例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 在此範例中，配接器會連線到資料庫"my_database 」，「 然後 」 資料庫執行個體，在本機電腦上。  
  
```  
mssql://localhost/sql_server_instance/my_database/  
```  
  
 在此範例中，配接器會連接到本機電腦上執行的預設執行個體的預設資料庫。  
  
```  
mssql://localhost///  
```  
  
 如需如何指定連接到 SQL Server 資料庫時您：  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到使用 SQL 配接器的 Visual Studio 中的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md)。  
  
- 設定傳送埠或接收埠 （位置） 中的 BizTalk Server 解決方案，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
- 程式設計解決方案中使用的 WCF 通道模型，請參閱 <<c0> [ 建立通道，使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)。  
  
- 程式設計解決方案中使用的 WCF 服務模型，請參閱 <<c0> [ 設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)