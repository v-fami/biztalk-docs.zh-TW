---
title: "設定 Siebel 系統的 WCF 用戶端 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, create a WCF client by specifying binding and endpoint address in a configuration file
- how to, create a WCF client by specifying binding and endpoint address in code
- WCF service model, configuring a WCF client for a Siebel system
ms.assetid: 6b4c5b06-d5ff-4dbf-8dc2-89c547a59864
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2395f8698c31a51466cfc98834cec137bf58a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-wcf-client-for-a-siebel-system"></a>設定 Siebel 系統的 WCF 用戶端
產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約為 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
 若要建立 WCF 用戶端，您必須指定端點位址和繫結。 端點位址必須包含有效的 Siebel 連接 URI，且繫結必須 Siebel 繫結執行個體 (**SiebelBinding**)。 如需有關 Siebel 連線 URI 的詳細資訊，請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)。  
  
 在您的程式碼或組態檔中，您可以指定 Siebel 繫結和端點位址。 當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。 這個檔案包含組態設定會反映的繫結屬性與連接資訊 （除了認證），您可以指定當您連接至 Siebel 系統具有[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端程式碼中指定的繫結和端點位址。 使用指定的 Siebel 認證的最佳作法是**ClientCredentials**的 WCF 用戶端，而不是連接的端點位址所提供的 URI 中的屬性。  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by using a binding object and endpoint address  
SiebelBinding sblBinding = new SiebelBinding();  
EndpointAddress sblAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu");  
  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient(sblBinding, sblAddress);  
  
    client.ClientCredentials.UserName.UserName = "SADMIN";  
    client.ClientCredentials.UserName.Password = "SADMIN";  
  
    client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a>在組態檔中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by specifying the client endpoint information in app.config  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
client.ClientCredentials.UserName.UserName = "SADMIN";  
client.ClientCredentials.UserName.Password = "SADMIN";  
  
client.Open();  
```  
  
### <a name="the-appconfig-file"></a>App.config 檔案  
 下列 XML 顯示時間戳記商務服務所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 此檔案包含在上述範例中所參考的用戶端端點組態。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <siebelBinding>  
                <binding name="SiebelBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    enablePerformanceCounters="false" enableConnectionPooling="true"  
                    maxConnectionsPerSystem="5" idleConnectionTimeout="00:01:00"  
                    acceptCredentialsInUri="false" />  
            </siebelBinding>  
        </bindings>  
        <client>  
            <endpoint address="siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu"  
                binding="siebelBinding" bindingConfiguration="SiebelBinding"  
                contract="BusinessServices_TimeStamp_Operation" name="SiebelBinding_BusinessServices_TimeStamp_Operation" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。 每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 Siebel 成品。例如，"SiebelBinding_BusinessServices_TimeStamp_Operation"。 如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。 這些繫結組態項目將會透過下列方式命名： SiebelBinding、 SiebelBinding1、 SiebelBinding2，依此類推。 在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)