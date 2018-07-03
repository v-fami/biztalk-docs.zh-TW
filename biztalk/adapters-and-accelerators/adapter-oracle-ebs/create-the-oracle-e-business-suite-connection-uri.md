---
title: 建立 Oracle E-business Suite 連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91eb49fa-2a69-470b-b96d-dc3a6ffafef6
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 238f1208d2a24a861c169aee448fd696bca2b34b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992847"
---
# <a name="create-the-oracle-e-business-suite-connection-uri"></a>建立 Oracle E-business Suite 連線 URI
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]連線 URI 包含配接器用來連接到 Oracle E-business Suite 和基本上是基礎的 Oracle 資料庫的屬性。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援連接到基礎的 Oracle 資料庫的兩種方式： 使用 tnsnames.ora，而不使用 tnsnames.ora。 根據一種連線方法，連線 URI 的格式是也不同。 本主題提供 Oracle 連線 URI 的相關資訊，並也提供其他主題連結，說明如何在不同的程式設計案例中指定的 URI。  

 Oracle E-business Suite 是一個應用程式層，介面為基礎的 Oracle 資料庫，並分類為不同的應用程式，例如財務和人力資源，根據組織內不同的需求。 每個應用程式提供各種 「 表單 」 可讓使用者為基礎的 Oracle 資料庫輸入資料。 以這些形式的存取權受到使用者與應用程式內容，包含使用者所屬的組織識別碼 」 負責 」 相關聯的使用者，以及 Oracle E-business Suite 應用程式的名稱建立關聯的使用者要叫用。 即使配接器會直接連線至基礎資料庫，並不會使用表單來與 Oracle E-business Suite，設定應用程式內容時，強制在 Oracle E-business Suite 成品上執行作業。 因此，若要連接到 Oracle E-business suite 和基礎 Oracle 資料庫、 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須：  

- 指定的連接來連接到 Oracle E-business Suite 和基礎的 Oracle 資料庫的 URI。 建立連線時，您可以選擇 Oracle E-business Suite 或基礎的 Oracle 資料庫中指定的認證。  

- 設定使用者的應用程式內容。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開特定的繫結屬性接受的認證和責任。 如需有關這些繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需設定應用程式內容的詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

  本節提供有關如何指定連線 URI 連線至使用 tnsnames.ora 的基礎資料庫，且未使用 tnsnames.ora 的資訊。 它也提供用於連接到 Oracle E-business Suite 連線 URI 的相關資訊。  

## <a name="connect-using-tnsnamesora"></a>使用 tnsnames.ora 連接  

> [!IMPORTANT]
> - 這種方法，您必須在電腦上的 tnsnames.ora 檔案中加入 net 的服務名稱項目，配接器用戶端安裝。 Net 服務名稱項目的相關資訊，請參閱[設定 E-business Suite 配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)。  
>   -   執行 Oracle 用戶端的限制，因為**DataSourceName**連線 URI 中的參數 （net 的服務名稱） 不能包含超過 39 個字元，如果您要在交易中執行作業。 因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。  

 連線 URI 可以包含用來識別您要連接的 Oracle E-business Suite 服務 Oracle net 的服務名稱。 Oracle 用戶端會根據 Oracle 命名方法，您將它設定為使用階層解析您在 Oracle E-business Suite 服務的連接資訊的連線 URI 中提供的 Oracle net 的服務名稱。 一種通用的命名方法會呼叫本機命名。 本機命名，Oracle 用戶端會使用一個稱為 tnsnames.ora 檔案，以解析 Oracle net 的服務名稱。  

 典型的端點位址 URI[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams`，其中：  

- 配置為配置名稱。  

- userauthparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊比方說，net 的服務名稱。  

  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 遵循這個基本的格式，並實作如下：  

```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]  
```  

 下表說明連線 URI 所包含的屬性。  


| 連線 URI 屬性 |    類別目錄    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [使用者名稱]       | userauthparams | 要用於驗證的使用者名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 可能值**ClientCredentialType**繫結屬性是**資料庫**並**EBusiness**。 根據此繫結屬性的值，您必須指定相關的認證。 如需詳細資訊，請參閱 < [Oracle 認證和連線 URI](#BKMK_OraCreds)。 **注意：** 您必須設定**AcceptCredentialsInUri**繫結屬性 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時，您輸入使用者名稱的值的大小寫。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入使用者名稱包含特殊字元，您必須指定雙引號括住的值。 |
|       [密碼]        | userauthparams |                                                                                要用於驗證的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定 Oracle 資料庫使用者的密碼。 如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 使用者的密碼。 **注意︰** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時，您輸入的密碼值的大小寫。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留密碼的情況，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。                                                                                |
|   [NET_SERVICE_NAME]    | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                                                    Net 的服務名稱的電腦上的 tnsnames.ora 檔案中指定其中[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]安裝。 如需 net 的服務名稱和 tnsnames.ora 的資訊，請參閱[設定 E-business Suite 配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)。                                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="connect-without-using-tnsnamesora"></a>不使用 tnsnames.ora 連接  

> [!IMPORTANT]
> - 這種方法，您不需要網路的服務名稱項目在 tnsnames.ora。 此外，您甚至不必有安裝配接器用戶端的電腦上的 tnsnames.ora 檔案。  
>   -   如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  

 典型的端點位址 URI[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams`，其中：  

- 配置為配置名稱。  

- userauthparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱、 連接埠號碼、 等等。  

  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 遵循這個基本的格式，並實作如下：  

```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/[SERVICE_TYPE]   
```  

 下表說明連線 URI 所包含的屬性。  


| 連線 URI 屬性 |    類別目錄    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [使用者名稱]       | userauthparams | 要用於驗證的使用者名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 可能值**ClientCredentialType**繫結屬性是**資料庫**並**EBusiness**。 根據此繫結屬性的值，您必須指定相關的認證。 如需詳細資訊，請參閱 < [Oracle 認證和連線 URI](#BKMK_OraCreds)。 **注意：** 您必須設定**AcceptCredentialsInUri**繫結屬性 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時，您輸入使用者名稱的值的大小寫。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入使用者名稱包含特殊字元，您必須指定雙引號括住的值。 |
|       [密碼]        | userauthparams |                                                                                要用於驗證的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定 Oracle 資料庫使用者的密碼。 如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 使用者的密碼。 **注意︰** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時，您輸入的密碼值的大小寫。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留密碼的情況，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。                                                                                |
|      [SERVER_NAME]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Oracle E-business Suite 執行所在的伺服器名稱。 這是必要項目。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|      [; PORT_NUMBER]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Oracle Net 接聽程式連接埠。 預設值 1521年。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|     [服務名稱]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Oracle 資料庫的服務名稱。 這是必要項目。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|     [SERVICE_TYPE]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Oracle 服務的型別。 可能的值為**專用**或是**共用**。 使用專用的服務會使用專用的伺服器的程序，提供只有一位使用者的程序。 共用的服務會使用可以提供多個使用者處理序共用的伺服器處理序。 預設值是**專用**。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

##  <a name="BKMK_OraCreds"></a> Oracle 認證和連線 URI  
 根據預設，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 中指定的 Oracle 認證時，會擲回例外狀況。 這是因為這些認證以純文字中的連線 URI，而這會造成安全性風險。 您可以設定**AcceptCredentialsInUri**屬性繫結至控制項是否連線 URI 可以包含的 Oracle 資料庫的認證。 如果**AcceptCredentialsInUri**屬性是**false**，這是預設值，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]時擲回例外狀況的連線 URI 包含 Oracle 認證; 如果屬性為 **，則為 true**，會擲回任何例外狀況。  

> [!IMPORTANT]
>  在字串中傳遞認證以純文字所造成的安全性風險，因為您應該避免在 連線 URI 中指定 Oracle 資料庫連接認證。 如需如何更安全的方式提供的 Oracle 資料庫的 認證的詳細資訊，請參閱[保護您的 Oracle EBS 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。  

 您也可以選擇指定的資料庫認證或 Oracle E-business Suite 的認證建立 Oracle E-business Suite 的連線。 配接器會公開三個繫結屬性，來啟用此行為： **ClientCredentialType**， **OracleUserName**， **OraclePassword**。  

 可能值**ClientCredentialType**繫結屬性是**資料庫**並**EBusiness**。  

-   如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定的資料庫認證。  

-   如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 認證。 在此情況下，配接器用戶端也必須指定的資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。  

> [!IMPORTANT]
>  在案例中，配接器用戶端指定的資料庫認證，來設定連線到 Oracle E-business Suite **ClientCredentialType**繫結屬性**資料庫**，但是叫用 OracleE-business Suite 成品，針對指定的值**OracleUserName**並**OraclePassword**繫結屬性用來設定應用程式內容。 設定應用程式內容，是叫用 Oracle E-business Suite 中的成品的必要項目。 如需設定應用程式內容的詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  

- 如果您要指定在 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

- 如果您指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

## <a name="using-the-connection-uri-to-connect-to-oracle-e-business-suite"></a>用於連接到 Oracle E-business Suite 連線 URI  
 以下是範例的連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 tnsnames.ora。  

```  
oracleebs://ADAPTER  
```  

 在此範例中，配接器是在 tnsnames.ora 目標 Oracle 資料庫的服務名稱和連接資訊與相關聯的 net 的服務名稱。  

 以下是範例的連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不用 tnsnames.ora。  

```  
oracleebs://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated  
```  

 在此範例中，伺服器名稱是"yourOracleServer 」，和服務名稱是"yourOracleDatabaseServiceName 」。  

 如需如何連接到 Oracle E-business Suite 的資訊時您：  

- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  

- 設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 <<c2> [ 手動設定 Oracle E-business 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  

## <a name="see-also"></a>另請參閱  
 [設定 Oracle 用戶端 E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)  
 [建立 Oracle E-business Suite 的連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)