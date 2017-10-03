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
# <a name="how-the-resolver-service-sample-works"></a><span data-ttu-id="1a1ea-102">解析程式服務範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="1a1ea-102">How the Resolver Service Sample Works</span></span>
<span data-ttu-id="1a1ea-103">解析程式服務範例會具現化解析程式服務，並傳遞您指定的訊息，進行處理。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-103">The Resolver Service sample instantiates the Resolver service and passes the message you specify to it for processing.</span></span> <span data-ttu-id="1a1ea-104">解析程式服務範例用戶端應用程式會使用第一個參數，做為 ResolverList.xml 檔案，其中包含多個的解析程式要求，並將這些要求傳送給解析程式服務的路徑。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-104">The Resolver Service sample client application uses the first parameter as the path to the ResolverList.xml file, which contains multiple resolver requests, and sends these requests to the Resolver service.</span></span> <span data-ttu-id="1a1ea-105">例如，以下是範例中使用 XPATH 要求。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-105">For example, the following is the XPATH request used in the sample.</span></span>  
  
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
>  <span data-ttu-id="1a1ea-106">實際內容**\<內容 >**項目不包含用來包裝在上述清單中的行泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-106">The actual content of the **\<Content>** element does not contain the white space characters used to wrap the lines in the preceding listing.</span></span>  
  
 <span data-ttu-id="1a1ea-107">上述清單會顯示要求包含解析程式設定連接字串內**\<內容 >**項目。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-107">The preceding listing shows that the request contains the resolver configuration connection string within a **\<Content>** element.</span></span> <span data-ttu-id="1a1ea-108">**\<主體 >**項目包含訊息主體。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-108">The **\<body>** element contains the message body.</span></span>  
  
 <span data-ttu-id="1a1ea-109">解析程式服務會使用**ResolverMgr**類別具現化解析程式類型的連接字串中所定義的適當解析程式的具象執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-109">The Resolver service uses the **ResolverMgr** class to instantiate a concrete instance of the appropriate resolver, defined by the resolver type in the connection string.</span></span> <span data-ttu-id="1a1ea-110">在 XPATH 要求時，這是 XPATH 解析程式。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-110">In the case of the XPATH request, this is the XPATH resolver.</span></span>  
  
 <span data-ttu-id="1a1ea-111">接下來，架構會建立執行個體**ResolveProvider**名為 ESB 類別。Resolver.XPath 來處理要求。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-111">Next, the framework creates an instance of the **ResolveProvider** class named ESB.Resolver.XPath to process the request.</span></span> <span data-ttu-id="1a1ea-112">用戶端應用程式會將回應訊息從解析程式服務寫入至名為 \Source\Samples\ResolverService\Output 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-112">The client application writes the response message from the Resolver service into the folder named \Source\Samples\ResolverService\Output.</span></span> <span data-ttu-id="1a1ea-113">下列清單顯示回應的內容。</span><span class="sxs-lookup"><span data-stu-id="1a1ea-113">The following listing shows the contents of the response.</span></span>  
  
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