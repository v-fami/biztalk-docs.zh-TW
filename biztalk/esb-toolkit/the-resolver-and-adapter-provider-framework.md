---
title: "解析器和配接器提供者架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717e7919b3f822ba582ea3c1e50f251eea18a06b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-and-adapter-provider-framework"></a>解析器和配接器提供者架構
解析器和配接器提供者架構支援路線、 轉換和端點解析和路由。 架構可以動態地解決端點，並設定輸出配接器屬性。 之後的解析程式元件會解析端點 （例如，使用通用描述、 探索與整合 [UDDI] 尋找傳出的 Web 服務端點），註冊配接器提供者元件設定的特定內容[!INCLUDE[prague](../includes/prague-md.md)]配接器。 例如，Wcf-basichttp 配接器提供者負責設定 BizTalk 特定訊息的端點 URI，將會使用特定的 BizTalk 配接器; 內容屬性FTP 配接器提供者會負責設定 FTP 配接器的特定屬性。  
  
 解析器和配接器提供者架構的其中一個目標是以支援解析度和路由在任一個訊息層級，而不需使用 BizTalk 協調流程，或在協調流程層級。 在這兩種情況下，可插式架構會提供簡易的開發、 部署和註冊新的解析程式和配接器提供者。 所有的解析程式和配接器提供者實作妥善定義之介面，並視需要載入執行階段時透過組態檔中註冊。  
  
 ESB 發送器和 ESB 發送器解譯管線元件會使用傳遞的連接字串從路線 SOAP 標頭或管線組態至解析程式管理員解析器和配接器提供者架構。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態包含的所有已註冊的解析程式和配接器提供者的詳細資料。 在執行的階段，解析程式管理員和配接器管理員從組態檔讀取的已註冊的解析程式和配接器提供者的詳細資料，載入適當的組件，並將其儲存在 BizTalk 主控件層級快取中。 此快取技術移除重複的組態檔的讀取和載入的組件的每一個提交訊息的需求。  
  
 如需有關如何解析器和配接器提供者架構的運作方式以及如何擴充它藉由建立自訂的解析程式和配接器提供者，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。  
  
## <a name="supported-resolution-mechanisms-resolvers"></a>支援的解析機制 （解析程式）  
 BizTalk ESB Toolkit 包含下列解析程式：**靜態、 UDDI、 UDDI3、 XPATH，BRE BRI、 路線，路線靜態**和**LDAP**。  
  
 解析程式的連接字串一律組成**moniker** (例如**BRE**) 後面接著":\\\\」 和連接或處理程序的詳細資料。 Moniker 符合相關聯的解析程式組態檔中的定義。 每個連接字串相關聯的屬性是唯一的而且並非所有的屬性不需要。 每個 「 解決者 」 的結構描述位於 ESB。Resolvers.Schemas 專案。  
  
 連接字串的範例如下：  
  
-   **靜態**  
  
     靜態：\\\TransportType=;  
  
     TransportLocation = http://localhost/ESB.CanadianServices/SubmitPOService.asmx;  
  
     動作 =;  
  
     EndPointConfig =;  
  
     JaxRpcResponse = false;  
  
     MessageExchangePattern =;  
  
     TargetNamespace = http://globalbank.esb.dynamicresolution.com/canadianservices/;  
  
     TransformType =;  
  
-   **UDDI**  
  
     UDDI:\\\serverUrl= http://localhost: 9901/rmengine;  
  
     serviceName = OrderPurchaseWebService;  
  
     serviceProvider = Microsoft 作法 ESB  
  
-   **XPATH**  
  
     \\\TransportType=;  
  
     TransportLocation = /*[local-name = 'OrderDoc' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name = 'ID' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/']。  
  
     動作 =;  
  
     EndPointConfig =;  
  
     JaxRpcResponse =;  
  
     MessageExchangePattern =;  
  
     TargetNamespace = /*[local-name = 'OrderDoc' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name = 'customerName' 和命名空間 uri （） ='http: / /globalbank.esb.dynamicresolution.com/northamericanservices/']。  
  
     TransformType =;  
  
-   **BRE**  
  
     BRE:\\\policy=GetCanadaEndPoint;  
  
     版本 =;  
  
     useMsg =;  
  
-   **BRI**  
  
     BRI:\\\policy=ResolveItinerary;  
  
     版本 =;  
  
     useMsg =;  
  
-   **路線**  
  
     行程：\\\name=TwoWayTestItinerary;  
  
     版本 =;  
  
-   **行程靜態**  
  
     行程靜態：\\\name=TwoWayTestItinerary;  
  
     版本 =;  
  
-   **LDAP**  
  
     LDAP:\\\TransportType=SMTP;  
  
     TransportLocation = {mail}  
  
     篩選 = (&amp;(objectClass = User) (&#124; (userPrincipalName =yourname@domain.com)));  
  
     SearchRoot =;  
  
     SearchScope = 樹狀子目錄。  
  
     EndpointConfig = Subject = {mail} 行程測試訊息&amp;  
  
     SMTPAuthenticate = 0&amp;  
  
     SMTPHost = 127.0.0.1&amp;  
  
     From =test@globalbank.com&amp;  
  
     DeliveryReceipt = false&amp;  
  
     MessagePartsAttachments = 0&amp;  
  
     ReadReceipt = false;  
  
     ThrowErrorIfNotFound = false;  
  
     動作 =;  
  
     JaxRpcResponse = false;  
  
     MessageExchangePattern =;  
  
     TargetNamespace =;  
  
     TransformType =;  
  
 並非所有的連接字串中的屬性是必要項。 此外， **EndPointConfig**是可以填入任何解析程式，並將傳回的特殊屬性。 （選擇性） 在解析程式可以儲存對應至特定的 BizTalk 配接器內容屬性，則亦可以寫入至 BizTalk 訊息內容的名稱/值組。  
  
 在此情況下， **ResolverDictionary**包含已解決的所有屬性的執行個體所傳回的解析程序則會傳遞配接器管理員。 配接器管理員會將字典傳遞給特定配接器提供者，將會設定所有配接器與端點特定 BizTalk 內容訊息屬性。 解析程式尋找**EndPointConfig**屬性，擷取對應到其各自的配接器 屬性的名稱/值組，並接著在訊息上設定這些值。  
  
## <a name="supported-adapter-providers"></a>支援的配接器提供者  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列內建配接器提供者：**檔案、 FTP、 SMTP、 MQSeries、 Wcf-basichttp、 Wcf-wshttp**和**Wcf-custom**。 每個配接器提供者的名稱是與 BizTalk Server 中的關聯配接器 （傳輸類型） 的名稱相同。  
  
 解析器和配接器提供者架構的主要優點是您可以透過建立並註冊您自己的自訂解析程式來解析端點資訊和自訂配接器提供者設定的已註冊的 BizTalk 配接器的特定屬性擴充它。 如需詳細資訊，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。