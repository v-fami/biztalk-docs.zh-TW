---
title: "解析程式服務範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33b5f886-ec54-4b2b-b09d-fb4c47ad43a5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c44677d4d488a4770c540ef94c0922579be3184
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-resolver-service-sample-works"></a>解析程式服務範例的運作方式
解析程式服務範例會具現化解析程式服務，並傳遞您指定的訊息，進行處理。 解析程式服務範例用戶端應用程式會使用第一個參數，做為 ResolverList.xml 檔案，其中包含多個的解析程式要求，並將這些要求傳送給解析程式服務的路徑。 例如，以下是範例中使用 XPATH 要求。  
  
```  
  
//XPATH  
<Resolver>  
  <name>XPATHWithFILE</name>   
  <Content>![CDATA[XPATH:\\TransportLocation=/*[local-name()='OrderDoc'   
    and namespace-uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/']/*[local-name()='ID' and namespace-  
    uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/'];TargetNamespace=;  
    MessageExchangePattern=;EndpointConfig=;JaxRpcResponse=;TransportType=;  
    Action=;TransformType=]]  
  </Content>   
  <body>  
    ![CDATA[   
    <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
      <ns0:customerName>Microsoft</ns0:customerName>  
  
<ns0:ID>FILE://C:\Projects\Microsoft.Practices.ESB\Source\Samples  
    \DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml</ns0:ID>   
      <ns0:requestType>10</ns0:requestType>   
    </ns0:OrderDoc>  
    ]]   
  </body>  
</Resolver>  
```  
  
> [!NOTE]
>  實際內容**\<內容 >**項目不包含用來包裝在上述清單中的行泛空白字元。  
  
 上述清單會顯示要求包含解析程式設定連接字串內**\<內容 >**項目。 **\<主體 >**項目包含訊息主體。  
  
 解析程式服務會使用**ResolverMgr**類別具現化解析程式類型的連接字串中所定義的適當解析程式的具象執行個體。 在 XPATH 要求時，這是 XPATH 解析程式。  
  
 接下來，架構會建立執行個體**ResolveProvider**名為 ESB 類別。Resolver.XPath 來處理要求。 用戶端應用程式會將回應訊息從解析程式服務寫入至名為 \Source\Samples\ResolverService\Output 的資料夾。 下列清單顯示回應的內容。  
  
```  
  
//XPATH  
Resolver.Action =   
Resolver.ActionField =   
Resolver.DocumentSpecName =   
Resolver.DocumentSpecStrongName =   
Resolver.EndpointConfig =   
Resolver.EpmRRCorrelationToken =   
Resolver.FixJaxRpc = False  
Resolver.InboundTransportLocation =   
Resolver.InboundTransportType =   
Resolver.InterchangeId =   
Resolver.IsRequestResponse =   
Resolver.MessageExchangePattern =   
Resolver.MessageType =   
Resolver.MethodName =   
Resolver.OutboundTransportCLSID =   
Resolver.ReceiveLocationName =   
Resolver.ReceivePortName =   
Resolver.Success = False  
Resolver.TargetNamespace =   
Resolver.TransformType =   
Resolver.TransportLocation = FILE://C:\Projects\Microsoft.  
    Practices.ESB\Source\Samples  
\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml  
Resolver.TransportNamespace =   
Resolver.TransportType = FILE  
Resolver.WindowUserField =  
```