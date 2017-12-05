---
title: "設定用戶端繫結為 SAP 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxy programming, creating a proxy
- creating a proxy
- how to, create a proxy
ms.assetid: bceef132-29ff-4207-a37d-bf94fab484dd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e9a4f84dbf98a17b2c1a918e30ab85b8e86c13
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="configure-a-client-binding-for-the-sap-system"></a>設定用戶端繫結為 SAP 系統
產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。 如需有關如何產生 WCF 用戶端類別和協助程式程式碼的作業資訊的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
 若要建立 WCF 用戶端，您必須指定端點位址和繫結。 端點位址必須包含有效的 SAP 連接 URI，而且繫結必須是 SAP 繫結執行個體 (**SAPBinding**)。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
 在您的程式碼或組態檔中，您可以指定 SAP 繫結和端點位址。 當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。 這個檔案包含反映的繫結屬性和連接資訊 （除了認證），當您連接至 SAP 系統時，您所指定的組態設定[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端程式碼中指定的繫結和端點位址。 使用指定的 SAP 系統認證的最佳作法是**ClientCredentials**的 WCF 用戶端，而不是連接的端點位址所提供的 URI 中的屬性。  
  
```  
// A WCF client that targets an RFC is created  
// by using a binding object and endpoint address  
SAPBinding sapBinding = new SAPBinding();  
EndpointAddress sapAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00");  
  
RfcClient rfcClient = new RfcClient(sapBinding, sapAddress);  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a>在組態檔中指定的繫結和端點位址  
 下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。  
  
```  
// A WCF client that targets an RFC is created  
// by specifying the client endpoint information in app.config  
RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
 下列 XML 顯示為 EMP 資料表所建立的組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 此檔案包含在上述範例中所參考的用戶端端點組態。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" receiveIdocFormat="Typed"  
                    generateFlatFileCompatibleIdocSchema="true" maxConnectionsPerSystem="50"  
                    enableConnectionPooling="true" idleConnectionTimeout="00:15:00"  
                    flatFileSegmentIndicator="SegmentDefinition" enablePerformanceCounters="false"  
                    autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false" padReceivedIdocWithSpaces="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="Rfc"  
                name="SAPBinding_Rfc" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。 每個 WCF 用戶端項目會有唯一的名稱，根據其繫結組態和目標 SAP 系統成品 （例如 Rfc 和 Trfc）;例如，"SAPBinding_Rfc"。 如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。 這些繫結組態項目將會透過下列方式命名： SAPBinding1、 SAPBinding2，依此類推。 在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。  
  
> [!IMPORTANT]
>  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現不同 SAP 成品 （例如 RFC、 TRFC 和 IDOC） 相同的類型做為相同的服務合約的不同作業。 例如，兩個不同的 Rfc、 RFC_EXAMPLE_A 和 RFC_EXAMPLE_B，會同時發生在相同的服務合約 (「 Rfc")。 這表示會在相同的 WCF 用戶端類別，所叫用這兩個 Rfc **RfcClient**，而且這兩個 Rfc 的參數會在相同的命名空間中宣告。 因此，您必須在相同產生 WCF 用戶端，這兩個 rfc[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]以避免當您建置方案時遇到的命名空間衝突的工作階段 （連線）。  
  
## <a name="see-also"></a>請參閱  
[開發使用 WCF 服務模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [產生 WCF 用戶端或 SAP 方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)   
 [建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)