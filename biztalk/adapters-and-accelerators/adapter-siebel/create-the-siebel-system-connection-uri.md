---
title: 建立 Siebel 系統連接 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI
- connecting to Siebel, using the connection URI
- how to, connect using connection URI
- connecting using connection URI
ms.assetid: 8cc78149-1c20-40db-aece-aab520ee04e7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3360433e97b9b7d21a06d3ad5c304f37a924589f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000615"
---
# <a name="create-the-siebel-system-connection-uri"></a>建立 Siebel 系統連線 URI
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]連線 URI 包含配接器用來連接到 Siebel 系統的屬性。  

 本主題提供有關 Siebel 連線 URI 的資訊，並也會提供說明如何在不同的程式設計案例中，指定連線 URI 的其他主題的連結。  

## <a name="connection-uri-for-the-siebel-adapter"></a>Siebel 配接器的連線 URI  
 一般[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]端點位址 URI 表示，如下所示：  

```  
scheme://userinfoparams@hostinfoparams?query_string  
```  

 端點位址 URI 包含下列元件：  

- 配置為配置名稱。  

- userinfoparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊例如，路徑。  

- query_string 是以問號 （？） 分隔的參數的選擇性名稱 / 值集合。  

  Siebel 連接 URI 會遵循下列一般格式，並實作如下：  

```  
siebel://Username=[USER_NAME];Password=[PASSWORD]@[SERVER]:[PORT]?SiebelObjectManager=[SIEBEL_OBJECT_MANAGER_NAME]&SiebelEnterpriseServer=[SERVER_NAME]&Language=[LANGUAGE]&Transport=[TRANSPORT]&Encryption=[ENCRYPTION]&Compression=[COMPRESSION]&SiebelServer=[SIEBEL_SERVER_NAME]&SiebelRepository=[SIEBEL_REPOSITORY_NAME]  
```  

 下列各節會說明實作 Siebel 連線 URI 的每個元件的屬性。  

### <a name="the-scheme-for-the-siebel-connection-uri"></a>Siebel 連接 URI 配置  
 Siebel 連線 URI 的配置是 「 siebel"。  

### <a name="user-information-in-the-siebel-connection-uri"></a>Siebel 連接 URI 中的使用者資訊  
 根據預設， [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] Siebel 系統的認證在 連線 URI 中指定時，會擲回例外狀況。 這是因為這些認證以純文字，有固有的安全性風險。 您可以設定**AcceptCredentialsInUri**屬性繫結至控制項是否連線 URI 可以包含的認證。 如果**AcceptCredentialsInUri**屬性是**false**，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]時擲回例外狀況的連線 URI 包含認證; 如果屬性為**true**，會擲不回任何例外狀況。  

> [!IMPORTANT]
>  在字串中傳遞認證以純文字所造成的固有的安全性風險，因為它是最好不要在 連線 URI 中指定 Siebel 系統認證。  

 有數種方式可提供 Siebel 系統認證，而不需要在 連線 URI 中指定它們。  

- 在程式碼中，您可以設定**ClientCredentials**適當物件上的屬性。  

- 當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您可以輸入的認證，方法是選取**安全性**索引標籤**設定配接器** 對話方塊。  

- 當您指定傳送埠或接收位置中的繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案中，您可以輸入的認證，選取**安全性**適當的對話方塊索引標籤。  

  Siebel 連接 URI 以進行使用者驗證所需的參數名稱 / 值集合中的使用者資訊 (userinfoparams)。 下表描述這些參數。  

| 屬性 |                                                                                                                                                                                                          描述                                                                                                                                                                                                          |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 使用者名稱 |      Siebel 系統; 中的使用者名稱這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]保留值，可以開啟 Siebel 系統上的連線時，您輸入使用者名稱的大小寫。       |
| [密碼] | Siebel 系統; 上使用者的密碼這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]保留大小寫的值，可以開啟 Siebel 系統上的連線時，您輸入的密碼。 |

### <a name="host-information-in-the-siebel-connection-uri"></a>Siebel 連接 URI 中的主機資訊  
 Siebel 主機資訊 (hostinfoparams) 指定 Siebel 系統的位址格式如下: [伺服器]: [連接埠]。 Siebel 伺服器版本中，根據 Siebel 主機資訊會採用不同的值：  

- **Siebel 7.5 和更早版本**，主應用程式資訊參數會採用哪些 Siebel 閘道伺服器安裝和 Siebel 閘道連接埠號碼之電腦的名稱。  

- **Siebel 7.7 或更新版本**，主機資訊參數會在其上安裝伺服器 Siebel 和 Siebel 連接 broker 連接埠號碼的電腦名稱。  

  > [!IMPORTANT]
  >  當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來連接到 Siebel 系統，必須提供主機資訊 」 SiebelGateway"連接屬性。  

### <a name="query-information-in-the-siebel-connection-uri"></a>Siebel 連接 URI 中的查詢資訊  
 Siebel 連接 URI 中的查詢資訊 (query_string) 用來指定其他連接屬性。  


|        屬性        |                                                                                                                                          描述                                                                                                                                           |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  SiebelObjectManager   |                                                                                                  企業伺服器上的 Siebel 物件管理員名稱。 此參數為必要。                                                                                                   |
| SiebelEnterpriseServer |                                                                                                             Siebel Enterprise Server 的名稱。 此參數為必要。                                                                                                              |
|        語言        |                                             物件管理員語言。 這個參數是選擇性的。 如果未指定，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供預設值 (cht)。                                              |
|       傳輸        |                                                                        傳輸方式;僅支援 tcpip。 這個參數是選擇性的。 如果未指定，Siebel 系統會提供預設值 (tcpip)。                                                                         |
|       加密       | 若要使用之間的加密類型[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統。 支援的值為 none、 mscrypto，或 rsa。 這個參數是選擇性的。 如果未指定，Siebel 系統會提供預設值 （無）。 |
|      壓縮更      |    之間使用的壓縮演算法[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統。 支援的值為 none 或 zlib。 這個參數是選擇性的。 如果未指定，Siebel 系統會提供預設值 (zlib)。     |
|      SiebelServer      |                                                                                 Siebel 伺服器。 所需的所有 Siebel 7.5 伺服器連接 (7.5.2、 7.5.3，等等。);否則，請勿設定此參數。                                                                                  |
|    SiebelRepository    |                          Siebel 儲存機制。 需要伺服器上是否有多個存放庫否則為選擇性。 **注意：** 如果伺服器上有多個存放庫，您必須指定一個目標存放庫 SiebelRepository 參數。                           |

 如需有關查詢資訊中所設定的 Siebel 參數的詳細資訊，請參閱您的 Siebel 文件。  

## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  

- 如果您要指定在 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

- 如果您指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

## <a name="using-the-connection-uri-to-connect-to-the-siebel-system"></a>使用連接至 Siebel 系統的連線 URI  
 以下是範例 Siebel 連線 URI。  

```  
siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu  
```  

> [!NOTE]
>  此範例的 URI 包含 Siebel 系統的認證;您必須設定**AcceptCredentialsInUri**繫結屬性 **，則為 true**若要使用的連接 URI，其中包含的認證。  

 如需如何連接到 Siebel 系統 （包括設定連接屬性） 當您：  

- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  

- 設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 <<c2> [ 手動設定 Siebel 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)。

- 程式設計解決方案中使用的 WCF 通道模型，請參閱 <<c0> [ 建立通道，使用 Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md)。  

- 程式設計解決方案中使用的 WCF 服務模型，請參閱 < [Siebel 系統設定 WCF 用戶端](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  

- 使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[for Siebel eBusiness 應用程式，使用 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)。  

## <a name="see-also"></a>另請參閱  
 [建立 Siebel 系統的連線](../../adapters-and-accelerators/adapter-siebel/create-a-connection-to-the-siebel-system.md)   
[開發您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)   
 [開發使用 WCF 通道 Model3 的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)   
 [開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)