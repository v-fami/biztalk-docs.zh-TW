---
title: "設定 Oracle 資料庫繫結的用戶端 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client binding, specifying in code
- WCF client, creating
- client binding, specifying in configuration file
ms.assetid: f18c7296-c28a-4dec-9514-5299c8c2dffe
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de5eeb9a7b0022ce4da5f56591e863f48bd0b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-oracle-database"></a>設定用戶端的 Oracle 資料庫繫結
產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
 若要建立 WCF 用戶端，您必須指定端點位址和繫結。 端點位址必須包含有效的 Oracle 連接 URI，且繫結必須是 Oracle 資料庫繫結執行個體 (**OracleDBBinding**)。 如需 Oracle 連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。 我們建議您不要指定使用者認證連線 URI 的一部分。 您可以改為使用**ClientCredentials** WCF 用戶端，如本主題所述的屬性。  
  
 在您的程式碼或組態檔中，您可以指定 Oracle 資料庫繫結與端點位址。 當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。 這個檔案包含反映的繫結屬性和連接資訊 （除了認證） 到與 Oracle 資料庫連接時，您指定的組態設定[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端程式碼中指定的繫結和端點位址。 使用指定的 Oracle 認證的最佳作法是**ClientCredentials**的 WCF 用戶端，而不是連接的端點位址所提供的 URI 中的屬性。  
  
```  
// A WCF client that targets the /SCOTT/EMP table is created  
// by using a binding object and endpoint address  
OracleDBBinding odbBinding = new OracleDBBinding();  
EndpointAddress odbAddress = new EndpointAddress("OracleDb://ADAPTER");  
  
SCOTTTableEMPClient empClient = new SCOTTTableEMPClient(odbBinding, odbAddress);  
  
empClient.ClientCredentials.UserName.UserName = "SCOTT";  
empClient.ClientCredentials.UserName.Password = "TIGER";  
  
empClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a>在組態檔中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。  
  
```  
// A WCF client that targets the /SCOTT/EMP table is created  
// by specifying the client endpoint information in app.config  
SCOTTTableEMPClient empClient = new SCOTTTableEMPClient("OracleDBBinding_SCOTT.Table.EMP");  
  
empClient.ClientCredentials.UserName.UserName = "SCOTT";  
empClient.ClientCredentials.UserName.Password = "TIGER";  
  
empClient.Open();  
```  
  
 下列 XML 顯示為 EMP 資料表所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 此檔案包含在上述範例中所參考的用戶端端點組態。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00"  
                    dataFetchSize="65536" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" longDatatypeColumnSize="32767" pollingStatement=""  
                    postPollStatement="" pollingInterval="500" useOracleConnectionPool="false"  
                    minPoolSize="1" maxPoolSize="100" incrPoolSize="5" decrPoolSize="1"  
                    connectionLifetime="0" transactionIsolationLevel="ReadCommitted"  
                    enablePerformanceCounters="false" acceptCredentialsInUri="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </oracleDBBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracledb://adapter/" binding="oracleDBBinding"  
                bindingConfiguration="OracleDBBinding" contract="SCOTTTableEMP"  
                name="OracleDBBinding_SCOTT.Table.EMP" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。 每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 Oracle 資料庫成品。例如，"OracleDBBinding_SCOTT。Table.EMP"。 如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。 這些繫結組態項目將會透過下列方式命名： OracleDBBinding1、 OracleDBBinding2，依此類推。 在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)   
 [為 Oracle 資料庫方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)   
 [建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)   
 [使用 WCF 通道模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)