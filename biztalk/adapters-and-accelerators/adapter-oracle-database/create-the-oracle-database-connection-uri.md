---
title: "建立 Oracle 資料庫連線 URI |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI, basic format of
- connection URI, database credentials and
- connection URI, connecting to the Oracle database
- connection URI
ms.assetid: 17d0a6d3-1b0c-43d6-a705-402c09a78ee0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f7b0fcc0c83bd4a844ac1a83488e1a3e8d9a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-oracle-database-connection-uri"></a>建立 Oracle 資料庫連線 URI
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]連線 URI 包含配接器用來連接到 Oracle 資料庫的屬性。 本主題提供有關如何指定要連接到 Oracle 資料庫使用 tnsnames.ora 且未使用 tnsnames.ora URI 的連接資訊。 它也提供使用連接到 Oracle 資料庫的連線 URI 的相關資訊。  
  
## <a name="connection-uri-to-connect-to-the-oracle-database-using-tnsnamesora"></a>連線來連接到 Oracle 資料庫使用 tnsnames.ora URI  
  
> [!IMPORTANT]
>  -   此方式，您必須新增網路服務名稱項目在 tnsnames.ora 檔案在電腦上安裝的配接器用戶端。 如需網路服務名稱項目，請參閱[設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)。  
> -   由於 Oracle 用戶端的限制， **DataSourceName**連線 URI 中的參數 (net service name) 不能包含超過 39 個字元，如果您在交易中執行的作業。 因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。  
  
 典型的端點位址 URI 中的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams?query_string`，其中：  
  
-   配置是配置名稱。  
  
-   userauthparams 是由端點所需的使用者驗證參數的名稱 / 值集合。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，路徑。  
  
-   query_string 是選擇性的問號 （？） 字元分隔的參數名稱 / 值集合。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：  
  
```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]?PollingId=[POLLING_ID]  
```  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|Description|  
|-----------------------------|--------------|-----------------|  
|[使用者名稱]|userauthparams|要用於驗證的 Oracle 資料庫; 上的使用者名稱例如，SCOTT。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **請注意**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供的 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫才:"SCOTT"。|  
|[密碼]|userauthparams|要用於 Oracle 資料庫上的驗證密碼例如，TIGER。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **請注意**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的密碼值的大小寫。 如需版本 10g 和更早版本，則 Oracle 系統上的密碼並不區分大小寫。|  
|[NET_SERVICE_NAME]|hostinfoparams|指定在 tnsnames.ora 檔案在電腦上的網路服務名稱其中[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]安裝。 如需網路服務名稱和 tnsnames.ora 的詳細資訊，請參閱[設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)。|  
|[POLLING_ID]|query_string|應該附加至 POLLINGSTMT 作業的標準命名空間的配接器的選擇性字串。 這可讓您的專案包含多個輪詢作業時，指定每個輪詢作業的唯一命名空間。 您沒有指定 PollingId 字串，如果您的專案包含只有一個 POLLINGSTMT 作業。|  
  
> [!NOTE]
>  查詢也會使用參數連接 URI 中指定端點位址時[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]中繼資料交換的用戶端。  
  
## <a name="connection-uri-to-connect-to-the-oracle-database-without-using-tnsnamesora"></a>連接到 Oracle 資料庫連接，而不使用 tnsnames.ora URI  
  
> [!IMPORTANT]
>  -   此方式，tnsnames.ora 檔案或實際 tnsnames.ora 檔案本身中的網路服務名稱不需要存在於用戶端電腦上。  
> -   如果您在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
 典型的端點位址 URI 中的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams?query_string`，其中：  
  
-   配置是配置名稱。  
  
-   userauthparams 是由端點所需的使用者驗證參數的名稱 / 值集合。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱、 連接埠號碼、 等等。  
  
-   query_string 是選擇性的問號 （？） 字元分隔的參數名稱 / 值集合。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：  
  
```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/SERVICE_TYPE]?PollingId=[POLLING_ID]  
```  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|Description|  
|-----------------------------|--------------|-----------------|  
|[使用者名稱]|userauthparams|要用於驗證的 Oracle 資料庫; 上的使用者名稱例如，SCOTT。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **請注意**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供的 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫才:"SCOTT"。|  
|[密碼]|userauthparams|要用於 Oracle 資料庫上的驗證密碼例如，TIGER。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **請注意**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留在開啟的 Oracle 資料庫上的連接時，您輸入的密碼值的大小寫。 如需版本 10g 和更早版本，則 Oracle 系統上的密碼並不區分大小寫。|  
|[SERVER_NAME]|hostinfoparams|Oracle 資料庫執行所在的伺服器名稱。 這是必要項目。|  
|[PORT_NUMBER]|hostinfoparams|Oracle 網路接聽程式連接埠。 如果未不指定任何值，配接器會採用預設值 1521年。|  
|[服務名稱]|hostinfoparams|Oracle 資料庫的服務名稱。 這是必要項目。|  
|[SERVICE_TYPE]|hostinfoparams|Oracle 服務型別。 可能的值為**專用**或**共用**。 專用的服務使用專用的伺服器處理序來服務只能有一個使用者處理序。 共用的服務會使用共用的伺服器程序可處理多個使用者處理序。 預設值是**專用**。|  
|[POLLING_ID]|query_string|應該附加至 POLLINGSTMT 作業的標準命名空間的配接器的選擇性字串。 這可讓您的專案包含多個輪詢作業時，指定每個輪詢作業的唯一命名空間。 您沒有指定 PollingId 字串，如果您的專案包含只有一個 POLLINGSTMT 作業。|  
  
> [!NOTE]
>  查詢也會使用參數連接 URI 中指定端點位址時[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]中繼資料交換的用戶端。  
  
## <a name="oracle-database-credentials-and-the-connection-uri"></a>Oracle 資料庫的認證和連線 URI  
 根據預設，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 中指定 Oracle 資料庫認證時，會擲回例外狀況。 這是因為這些認證表示為純文字格式的連線 URI，而這會造成安全性風險。 您可以設定**AcceptCredentialsInUri**屬性繫結至控制項是否連線 URI 可以包含 Oracle 資料庫的認證。 如果**AcceptCredentialsInUri**屬性是**false**、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]時擲回例外狀況的連線 URI 包含 Oracle 資料庫的認證; 如果屬性是**，則為 true**，擲回任何例外狀況。 有幾個少數的情況下，它是必要的連線 URI，指定認證例如，接收輸入的 POLLINGSTMT 作業，當您使用 WCF 服務模型或 WCF 通道模型。 大部分的情況下，不過，您應該避免提供連線 URI 中的認證。 如需如何以更安全的方式提供的認證將 Oracle 資料庫的詳細資訊，請參閱[保護 Oracle 資料庫應用程式安全](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)。  
  
> [!IMPORTANT]
>  在字串中傳遞認證以純文字所造成的安全性風險，因為您應該避免在連線 URI 中指定 Oracle 資料庫連接認證。  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援指定的連接有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  
  
-   如果您要指定中的 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
-   如果您所指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
## <a name="using-the-connection-uri-to-connect-to-the-oracle-database"></a>若要連接到 Oracle 資料庫使用的連線 URI  
 下列是連線 URI 的範例如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|使用 tnsnames.ora|不使用 tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER`<br /><br /> 在此範例中，配接器是在 tnsnames.ora 目標 Oracle 資料庫的服務名稱和連接資訊與相關聯的網路服務名稱。|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated`<br /><br /> 在此範例中，伺服器名稱是"yourOracleServer"，服務名稱是"yourOracleDatabaseServiceName"。|  
  
 以下是連線的 POLLINGSTMT 作業 URI 的範例。 此 URI 包含 PollingId 參數修改 POLLINGSTMT 作業的命名空間。  
  
|使用 tnsnames.ora|不使用 tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER?PollingId=MyPollingNotification1`|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated? PollingId=MyPollingNotification1`|  
  
 上述的連線 Uri、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立 POLLINGSTMT 作業的下列命名空間。  
  
```  
http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTMyPollingNotification1  
```  
  
 如需如何連接到 Oracle 資料庫時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
-   設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。  
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立使用 Oracle 資料庫的通道](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[設定 Oracle 資料庫繫結的用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)。  
  
-   使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[Oracle 資料庫與 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
[建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)   
 [設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)