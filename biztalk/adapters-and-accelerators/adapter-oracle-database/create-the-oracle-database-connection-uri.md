---
title: 建立 Oracle 資料庫連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI, basic format of
- connection URI, database credentials and
- connection URI, connecting to the Oracle database
- connection URI
ms.assetid: 17d0a6d3-1b0c-43d6-a705-402c09a78ee0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee680c0e27f0d5456c54701c4f385b2c629e146
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975871"
---
# <a name="create-the-oracle-database-connection-uri"></a>建立 Oracle 資料庫連線 URI
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]連線 URI 包含配接器用來連接到 Oracle 資料庫的屬性。 本主題提供有關如何指定連線 URI 連線至 Oracle 資料庫使用 tnsnames.ora 且未使用 tnsnames.ora 的資訊。 它也會提供連接到 Oracle 資料庫使用的連線 URI 的相關資訊。  

## <a name="connection-uri-to-connect-to-the-oracle-database-using-tnsnamesora"></a>連線來連接到 Oracle 資料庫使用 tnsnames.ora 的 URI  

> [!IMPORTANT]
> - 這種方法，您必須在電腦上的 tnsnames.ora 檔案中加入 net 的服務名稱項目，配接器用戶端安裝。 Net 服務名稱項目的相關的詳細資訊，請參閱[設定 Oracle 資料庫配接器對 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)。  
>   -   執行 Oracle 用戶端的限制，因為**DataSourceName**連線 URI 中的參數 （net 的服務名稱） 不能包含超過 39 個字元，如果您要在交易中執行作業。 因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。  

 典型的端點位址 URI[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams?query_string`，其中：  

- 配置為配置名稱。  

- userauthparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊例如，路徑。  

- query_string 是以問號 （？） 分隔的參數的選擇性名稱 / 值集合。  

  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 遵循這個基本的格式，並實作如下：  

```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]?PollingId=[POLLING_ID]  
```  

 下表說明連線 URI 所包含的屬性。  


| 連線 URI 屬性 |    類別目錄    |                                                                                                                                                                                                                                                                                                                                                                                           描述                                                                                                                                                                                                                                                                                                                                                                                            |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [使用者名稱]       | userauthparams | 要用於驗證的 Oracle 資料庫中; 上的使用者名稱比方說，SCOTT。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **附註**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留開啟的 Oracle 資料庫上的連接時，您輸入使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫:"SCOTT"。 |
|       [密碼]        | userauthparams |                                                                                                                                使用 Oracle 資料庫上進行驗證的密碼比方說，TIGER。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **附註**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會保留在開啟的 Oracle 資料庫上的連接時，您輸入密碼的值的大小寫。 如需版本 10g 及更早版本，則 Oracle 系統上的密碼並不區分大小寫。                                                                                                                                |
|   [NET_SERVICE_NAME]    | hostinfoparams |                                                                                                                                                                            Net 的服務名稱的電腦上的 tnsnames.ora 檔案中指定其中[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]安裝。 如需有關 net 的服務名稱和 tnsnames.ora 的詳細資訊，請參閱[設定 Oracle 資料庫配接器對 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)。                                                                                                                                                                             |
|      [POLLING_ID]       |  query_string  |                                                                                                                                                                                                                     選擇性的字串應該附加至 POLLINGSTMT 作業的標準命名空間的配接器。 這可讓您的專案包含多個輪詢作業時，指定每個輪詢作業的唯一命名空間。 您不必指定 PollingId 字串，如果您的專案包含只有一個 POLLINGSTMT 作業。                                                                                                                                                                                                                      |

> [!NOTE]
>  查詢參數也會在 URI 的連接時指定端點位址[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]中繼資料交換用戶端。  

## <a name="connection-uri-to-connect-to-the-oracle-database-without-using-tnsnamesora"></a>連線來連接到 Oracle 資料庫，而不需使用 tnsnames.ora 的 URI  

> [!IMPORTANT]
> - 這種方法，tnsnames.ora 檔案或實際 tnsnames.ora 檔案本身中的 net 的服務名稱不需要存在於用戶端電腦上。  
>   -   如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  

 典型的端點位址 URI[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams?query_string`，其中：  

- 配置為配置名稱。  

- userauthparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱、 連接埠號碼、 等等。  

- query_string 是以問號 （？） 分隔的參數的選擇性名稱 / 值集合。  

  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 遵循這個基本的格式，並實作如下：  

```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/SERVICE_TYPE]?PollingId=[POLLING_ID]  
```  

 下表說明連線 URI 所包含的屬性。  


| 連線 URI 屬性 |    類別目錄    |                                                                                                                                                                                                                                                                                                                                                                                           描述                                                                                                                                                                                                                                                                                                                                                                                            |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [使用者名稱]       | userauthparams | 要用於驗證的 Oracle 資料庫中; 上的使用者名稱比方說，SCOTT。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **附註**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]保留開啟的 Oracle 資料庫上的連接時，您輸入使用者名稱值的大小寫。 Oracle 資料庫上的使用者名稱會區分大小寫。 您應該確定您提供 Oracle 使用者名稱，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫所預期的情況下。 一般而言，這表示在 SCOTT/TIGER 認證中的使用者名稱應該是大寫:"SCOTT"。 |
|       [密碼]        | userauthparams |                                                                                                                                使用 Oracle 資料庫上進行驗證的密碼比方說，TIGER。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。<br /><br /> **附註**[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會保留在開啟的 Oracle 資料庫上的連接時，您輸入密碼的值的大小寫。 如需版本 10g 及更早版本，則 Oracle 系統上的密碼並不區分大小寫。                                                                                                                                |
|      [SERVER_NAME]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                          Oracle 資料庫執行所在的伺服器名稱。 這是必要項目。                                                                                                                                                                                                                                                                                                                                                          |
|      [; PORT_NUMBER]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                Oracle Net 接聽程式連接埠。 如果未不指定任何值，則配接器會採用預設值 1521年。                                                                                                                                                                                                                                                                                                                                                 |
|     [服務名稱]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                       Oracle 資料庫的服務名稱。 這是必要項目。                                                                                                                                                                                                                                                                                                                                                                       |
|     [SERVICE_TYPE]      | hostinfoparams |                                                                                                                                                                                                                                                  Oracle 服務的型別。 可能的值為**專用**或是**共用**。 使用專用的服務會使用專用的伺服器的程序，提供只有一位使用者的程序。 共用的服務使用的共用的伺服器處理序可以有多個使用者處理序。 預設值是**專用**。                                                                                                                                                                                                                                                   |
|      [POLLING_ID]       |  query_string  |                                                                                                                                                                                                                     選擇性的字串應該附加至 POLLINGSTMT 作業的標準命名空間的配接器。 這可讓您的專案包含多個輪詢作業時，指定每個輪詢作業的唯一命名空間。 您不必指定 PollingId 字串，如果您的專案包含只有一個 POLLINGSTMT 作業。                                                                                                                                                                                                                      |

> [!NOTE]
>  查詢參數也會在 URI 的連接時指定端點位址[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]中繼資料交換用戶端。  

## <a name="oracle-database-credentials-and-the-connection-uri"></a>Oracle 資料庫的認證和連線 URI  
 根據預設，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 中指定 Oracle 資料庫認證時，會擲回例外狀況。 這是因為這些認證以純文字中的連線 URI，而這會造成安全性風險。 您可以設定**AcceptCredentialsInUri**屬性繫結至控制項是否連線 URI 可以包含的 Oracle 資料庫的認證。 如果**AcceptCredentialsInUri**屬性是**false**，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]時擲回例外狀況的連線 URI 包含 Oracle 資料庫的認證; 如果屬性是 **，則為 true**，會擲回任何例外狀況。 有幾個少數的情況下，它是必要的連線 URI; 中指定認證例如，接收輸入的 POLLINGSTMT 作業，當您使用 WCF 服務的 WCF 通道模型。 大部分的情況下，不過，您應該避免提供連線 URI 中的認證。 如需如何更安全的方式提供的 Oracle 資料庫的 認證的詳細資訊，請參閱[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)。  

> [!IMPORTANT]
>  在字串中傳遞認證以純文字所造成的安全性風險，因為您應該避免在 連線 URI 中指定 Oracle 資料庫連接認證。  

## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  

- 如果您要指定在 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

- 如果您指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

## <a name="using-the-connection-uri-to-connect-to-the-oracle-database"></a>若要連接到 Oracle 資料庫使用的連線 URI  
 以下是範例的連線 URI 的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  

|使用 tnsnames.ora|不使用 tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER`<br /><br /> 在此範例中，配接器是在 tnsnames.ora 目標 Oracle 資料庫的服務名稱和連接資訊與相關聯的 net 的服務名稱。|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated`<br /><br /> 在此範例中，伺服器名稱是"yourOracleServer 」，和服務名稱是"yourOracleDatabaseServiceName 」。|  

 以下是連線的 POLLINGSTMT 作業 URI 的範例。 此 URI 包含 PollingId 參數修改 POLLINGSTMT 作業的命名空間。  

|使用 tnsnames.ora|不使用 tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER?PollingId=MyPollingNotification1`|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated? PollingId=MyPollingNotification1`|  

 上述的連接 Uri，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立 POLLINGSTMT 作業的下列命名空間。  

```  
http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTMyPollingNotification1  
```  

 如需如何連接到 Oracle 資料庫時您：  

- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  

- 設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 <<c2> [ 手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。  

- 程式設計解決方案中使用的 WCF 通道模型，請參閱 <<c0> [ 建立通道，使用 Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。  

- 程式設計解決方案中使用的 WCF 服務模型，請參閱 <<c0> [ 設定用戶端的 Oracle 資料庫繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)。  

- 使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[ServiceModel Metadata Utility Tool 與 BizTalk 配接器用於 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)。  

## <a name="see-also"></a>另請參閱  
[建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)   
 [設定 Oracle 用戶端，Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)