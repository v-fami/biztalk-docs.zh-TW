---
title: "建立 Oracle E-business Suite 連線 URI |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91eb49fa-2a69-470b-b96d-dc3a6ffafef6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3f6e3be6604e8786ff9481ab463f27a31bf1e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-oracle-e-business-suite-connection-uri"></a>建立 Oracle E-business Suite 連線 URI
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]連線 URI 包含配接器用來連接到 Oracle E-business Suite 和基本上基礎 Oracle 資料庫的屬性。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援基礎的 Oracle 資料庫連接的兩種方式： 使用 tnsnames.ora 且未使用 tnsnames.ora。 根據連線方法的類型，連線 URI 的格式是也不同。 本主題提供 Oracle 連接 URI 的相關資訊，並也提供其他主題連結，說明如何在不同的程式設計案例中指定的 URI。  
  
 Oracle E-business Suite 會是一個應用程式層級，介面與基礎的 Oracle 資料庫，並會分類成不同的應用程式，例如財務和 HR、 根據組織內不同的需求。 每個這些應用程式提供各種 「 表單 」 可讓使用者輸入資料為基礎的 Oracle 資料庫。 這些表單的存取權受限於使用者與應用程式內容可包含使用者所屬的組織 ID"責任"相關聯的使用者，以及 Oracle E-business Suite 應用程式的名稱建立關聯的使用者要叫用。 即使配接器會直接連線至基礎資料庫，且不使用表單來與 Oracle E-business Suite 介面，設定應用程式內容時，強制對 Oracle E-business Suite 成品執行作業。 因此，為了連接到 Oracle E-business suite，Oracle 資料庫的基礎，使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須：  
  
-   指定 URI 要連接到 Oracle E-business Suite 和基礎的 Oracle 資料庫的連線。 時建立的連接，您可以選擇指定 Oracle E-business Suite 為基礎的 Oracle 資料庫的認證。  
  
-   設定使用者的應用程式內容。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開可接受認證和責任的特定繫結屬性。 如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關如何設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 本節提供有關如何指定連接來連接使用 tnsnames.ora 基礎資料庫而不使用 tnsnames.ora 的 URI 資訊。 它也提供使用連接到 Oracle E-business Suite 連線 URI 的相關資訊。  
  
## <a name="connect-using-tnsnamesora"></a>使用 tnsnames.ora 連接  
  
> [!IMPORTANT]
>  -   此方式，您必須新增網路服務名稱項目在 tnsnames.ora 檔案在電腦上安裝的配接器用戶端。 如需網路服務名稱項目資訊，請參閱[設定 Oracle E-business Suite 配接器用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)。  
> -   由於 Oracle 用戶端的限制， **DataSourceName**連線 URI 中的參數 (net service name) 不能包含超過 39 個字元，如果您在交易中執行的作業。 因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。  
  
 連線 URI 可以包含用來識別您想要連接的 Oracle E-business Suite 服務的 Oracle 網路服務名稱。 Oracle 用戶端會根據 Oracle 命名方法，您將它設定為使用階層解析您提供 Oracle E-business Suite 服務的連接資訊連接 URI 中的 Oracle 網路服務名稱。 一種通用的命名方法會呼叫本機命名。 在本機命名，Oracle 用戶端會使用一個稱為 tnsnames.ora 檔案，以解析 Oracle net 服務名稱。  
  
 典型的端點位址 URI 中的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams`，其中：  
  
-   配置是配置名稱。  
  
-   userauthparams 是由端點所需的使用者驗證參數的名稱 / 值集合。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，網路服務名稱。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：  
  
```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]  
```  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|Description|  
|-----------------------------|--------------|-----------------|  
|[使用者名稱]|userauthparams|要用於驗證的使用者名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 可能值**ClientCredentialType**繫結屬性是**資料庫**和**EBusiness**。 這個繫結屬性的值，而定，您必須指定相關的認證。 如需詳細資訊，請參閱[Oracle 認證和連線 URI](#BKMK_OraCreds)。 **注意：**必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。 **注意：** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入使用者名稱連接到 Oracle E-business Suite 時的值的大小寫。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入含有特殊字元的使用者名稱，您必須指定雙引號括住的值。|  
|[密碼]|userauthparams|要用於驗證的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定 Oracle 資料庫使用者的密碼。 如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 使用者的密碼。 **注意：** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時輸入密碼的值的大小寫。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的密碼的大小寫，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。|  
|[NET_SERVICE_NAME]|hostinfoparams|指定在 tnsnames.ora 檔案在電腦上的網路服務名稱其中[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]安裝。 網路服務名稱和 tnsnames.ora 的相關資訊，請參閱[設定 Oracle E-business Suite 配接器用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)。|  
  
## <a name="connect-without-using-tnsnamesora"></a>不使用 tnsnames.ora 連接  
  
> [!IMPORTANT]
>  -   此方式，您不需要的網路服務名稱項目在 tnsnames.ora。 此外，您甚至不必 tnsnames.ora 檔案在電腦上的已安裝的配接器用戶端。  
> -   如果您在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
 典型的端點位址 URI 中的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]會表示為： `scheme://userauthparams@hostinfoparams`，其中：  
  
-   配置是配置名稱。  
  
-   userauthparams 是由端點所需的使用者驗證參數的名稱 / 值集合。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，伺服器名稱、 連接埠號碼、 等等。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 遵循這個基本格式與實作，如下所示：  
  
```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/[SERVICE_TYPE]   
```  
  
 下表說明連線 URI 所包含的屬性。  
  
|連線 URI 屬性|類別目錄|Description|  
|-----------------------------|--------------|-----------------|  
|[使用者名稱]|userauthparams|要用於驗證的使用者名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 可能值**ClientCredentialType**繫結屬性是**資料庫**和**EBusiness**。 這個繫結屬性的值，而定，您必須指定相關的認證。 如需詳細資訊，請參閱[Oracle 認證和連線 URI](#BKMK_OraCreds)。 **注意：**必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。 **注意：** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入使用者名稱連接到 Oracle E-business Suite 時的值的大小寫。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入含有特殊字元的使用者名稱，您必須指定雙引號括住的值。|  
|[密碼]|userauthparams|要用於驗證的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結指定的用戶端指定要連接的 Oracle 用戶端認證類型的屬性。 如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定 Oracle 資料庫使用者的密碼。 如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 使用者的密碼。 **注意：** [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留連接到 Oracle E-business Suite 時輸入密碼的值的大小寫。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的密碼的大小寫，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。|  
|[SERVER_NAME]|hostinfoparams|Oracle E-business Suite 執行所在的伺服器名稱。 這是必要項目。|  
|[PORT_NUMBER]|hostinfoparams|Oracle 網路接聽程式連接埠。 預設值 1521年。|  
|[服務名稱]|hostinfoparams|Oracle 資料庫的服務名稱。 這是必要項目。|  
|[SERVICE_TYPE]|hostinfoparams|Oracle 服務型別。 可能的值為**專用**或**共用**。 專用的服務使用專用的伺服器處理序來服務只能有一個使用者處理序。 共用的服務會使用共用的伺服器處理序可處理多個使用者處理序。 預設值是**專用**。|  
  
##  <a name="BKMK_OraCreds"></a>Oracle 認證和連線 URI  
 根據預設，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連線 URI 中指定的 Oracle 認證時，會擲回例外狀況。 這是因為這些認證表示為純文字格式的連線 URI，而這會造成安全性風險。 您可以設定**AcceptCredentialsInUri**屬性繫結至控制項是否連線 URI 可以包含 Oracle 資料庫的認證。 如果**AcceptCredentialsInUri**屬性是**false**，這是預設值，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]時擲回例外狀況的連線 URI 包含 Oracle 認證，如果屬性是**true**，擲回任何例外狀況。  
  
> [!IMPORTANT]
>  在字串中傳遞認證以純文字所造成的安全性風險，因為您應該避免在連線 URI 中指定 Oracle 資料庫連接認證。 如需如何以更安全的方式提供的認證將 Oracle 資料庫的詳細資訊，請參閱[安全應用程式 Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。  
  
 您也可以選擇指定的資料庫認證或 Oracle E-business Suite 認證連接到 Oracle E-business Suite 的資訊。 配接器會公開三個繫結屬性，以啟用這項行為： **ClientCredentialType**， **OracleUserName**， **OraclePassword**。  
  
 可能值**ClientCredentialType**繫結屬性是**資料庫**和**EBusiness**。  
  
-   如果**ClientCredentialType**屬性設定為**資料庫**，用戶端必須指定的資料庫認證。  
  
-   如果**ClientCredentialType**屬性設定為**EBusiness**，用戶端必須指定 Oracle E-business Suite 認證。 在此情況下，配接器用戶端也必須指定的資料庫認證**OracleUserName**和**OraclePassword**繫結屬性。  
  
> [!IMPORTANT]
>  在案例中，配接器用戶端指定的資料庫認證連接到 Oracle E-business Suite，藉由設定**ClientCredentialType**內容繫結至**資料庫**，但叫用 OracleE-business Suite 成品的指定值**OracleUserName**和**OraclePassword**繫結屬性用來設定應用程式內容。 設定應用程式內容是必要的叫用 Oracle E-business Suite 中的成品。 如需有關如何設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援指定的連接有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  
  
-   如果您要指定中的 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
-   如果您所指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
## <a name="using-the-connection-uri-to-connect-to-oracle-e-business-suite"></a>使用連接到 Oracle E-business Suite 連線 URI  
 下列是連線 URI 的範例如[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 tnsnames.ora。  
  
```  
oracleebs://ADAPTER  
```  
  
 在此範例中，配接器是在 tnsnames.ora 目標 Oracle 資料庫的服務名稱和連接資訊與相關聯的網路服務名稱。  
  
 下列是連線 URI 的範例如[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不用 tnsnames.ora。  
  
```  
oracleebs://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated  
```  
  
 在此範例中，伺服器名稱是"yourOracleServer"，服務名稱是"yourOracleDatabaseServiceName"。  
  
 如需有關如何連接到 Oracle E-business Suite 資訊時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
-   設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[手動設定 Oracle E-business 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Oracle E-business Suite 配接器用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)  
 [建立 Oracle E-business Suite 連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)