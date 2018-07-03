---
title: ESB 解析程式和配接器提供者架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95134a1f806398f14a5596149eb605e2de20cac2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002799"
---
# <a name="the-resolver-and-adapter-provider-framework"></a>解析程式和配接器提供者架構
解析程式和配接器提供者架構支援路線、 轉換和端點解析和路由。 架構可以動態地解析端點，並設定輸出配接器屬性。 之後的解析程式元件會解析端點 （例如，使用通用描述、 探索與整合 [UDDI] 來查看輸出的 Web 服務端點），配接器提供者元件會設定已註冊的 BizTalk Server 的特定屬性配接器。 比方說，Wcf-basichttp 配接器提供者負責設定 BizTalk 特定訊息的端點 URI，將會使用特定的 BizTalk 配接器; 的內容屬性FTP 配接器提供者會負責設定的 FTP 配接器的特定屬性。  
  
 解析程式和配接器提供者架構的其中一個目標是支援解析和路由在任一個傳訊層級，而不需使用 BizTalk 協調流程，或在協調流程層級。 在這兩種情況下，隨插即用的架構會提供簡易的開發、 部署和註冊新的解析程式和配接器提供者。 所有的解析程式和配接器提供者實作定義完善的介面，並會在執行階段透過組態檔中註冊的需求載入。  
  
 ESB 發送器和 ESB 發送器解譯管線元件使用的解析程式和配接器提供者架構，藉由傳遞路線 SOAP 標頭或管線組態到解析程式管理員的連接字串。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態包含的所有已註冊的解析程式和配接器提供者的詳細資料。 在執行的階段、 解析程式管理員和配接器管理員讀取組態檔中的已註冊的解析程式和配接器提供者的詳細資料的內容，載入適當的組件，並將它們儲存在 BizTalk 主控件層級快取檔案。 此快取技術中移除重複的組態檔的讀取和載入之組件的每個已提交之訊息的需求。  
  
 如需有關如何解析器和配接器提供者架構的運作方式以及如何擴充它藉由建立自訂解析程式和配接器提供者，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。  
  
## <a name="supported-resolution-mechanisms-resolvers"></a>支援的解析機制 （解析程式）  
 BizTalk ESB 工具組包含下列的解析程式：**靜態、 UDDI、 UDDI3、 XPATH，BRE、 BRI、 路線，路線靜態**並**LDAP**。  
  
 永遠包含解析程式的連接字串**moniker** (例如**BRE**) 後面接著":\\\\」 和連接或處理程序的詳細資料。 Moniker 會比對相關聯的解析程式組態檔中的定義。 每個連接字串相關聯的屬性是唯一的而且需要不是所有屬性。 解析程式的每個結構描述位於 ESB。Resolvers.Schemas 專案。  
  
 連接字串的範例如下：  
  
- **靜態**  
  
   STATIC:\\\TransportType=;  
  
   TransportLocation =<http://localhost/ESB.CanadianServices/SubmitPOService.asmx>;  
  
   Action=;  
  
   EndPointConfig=;  
  
   JaxRpcResponse=false;  
  
   MessageExchangePattern=;  
  
   TargetNamespace=<http://globalbank.esb.dynamicresolution.com/canadianservices/>;  
  
   TransformType=;  
  
- **UDDI**  
  
   UDDI:\\\serverUrl=<http://localhost:9901/rmengine>;  
  
   serviceName=OrderPurchaseWebService;  
  
   serviceProvider=Microsoft Practices ESB  
  
- **XPATH**  
  
   XPATH:\\\TransportType=;  
  
   `TransportLocation=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='ID' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   Action=;  
  
   EndPointConfig=;  
  
   JaxRpcResponse=;  
  
   MessageExchangePattern=;  
  
   `TargetNamespace=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='customerName' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   TransformType=;  

- **BRE**  
  
   BRE:\\\policy=GetCanadaEndPoint;  
  
   version=;  
  
   useMsg=;  
  
- **BRI**  
  
   BRI:\\\policy=ResolveItinerary;  
  
   version=;  
  
   useMsg=;  
  
- **路線**  
  
   ITINERARY:\\\name=TwoWayTestItinerary;  
  
   version=;  
  
- **路線-靜態**  
  
   路線靜態：\\\name=TwoWayTestItinerary;  
  
   version=;  
  
- **LDAP**  
  
   LDAP:\\\TransportType=SMTP;  
  
   TransportLocation={mail}  
  
   篩選 = (&(objectClass=User) (| (userPrincipalName =yourname@domain.com)));  
  
   SearchRoot=;  
  
   SearchScope=Subtree;  
  
   EndpointConfig = Subject = {郵件} 路線測試訊息 （& s) 
  
   SMTPAuthenticate = 0 （& s)
  
   SMTPHost = 127.0.0.1 （& s)
  
   From =test@globalbank.com（& s)
  
   DeliveryReceipt = false （& s)
  
   MessagePartsAttachments = 0 （& s)
  
   ReadReceipt=false;  
  
   ThrowErrorIfNotFound=false;  
  
   Action=;  
  
   JaxRpcResponse=false;  
  
   MessageExchangePattern=;  
  
   TargetNamespace=;  
  
   TransformType=;  
  
  並非所有的連接字串中的屬性是必要項目。 颾魤 ㄛ **EndPointConfig**是特殊的屬性，可以填入任何解析程式，並將其傳回。 （選擇性） 在解析程式可以儲存對應至特定的 BizTalk 配接器內容屬性，它反而可以寫入 BizTalk 訊息內容的名稱/值組。  
  
  在此情況下， **ResolverDictionary**包含已解析的所有屬性的執行個體解析程序然後傳遞回到配接器管理員。 配接器管理員會將字典傳遞至會設定所有配接器與端點特定 BizTalk 內容訊息屬性的特定配接器提供者。 解析程式尋找**EndPointConfig**屬性，擷取對應到其各自的配接器 屬性的名稱/值組，並接著在訊息上設定這些值。  
  
## <a name="supported-adapter-providers"></a>支援的配接器提供者  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包括下列的內建配接器提供者：**檔案、 FTP、 SMTP、 MQSeries、 Wcf-basichttp、 Wcf-wshttp**並**Wcf-custom**。 每個配接器提供者的名稱完全相同的 BizTalk Server 中的相關聯配接器 （傳輸類型） 的名稱。  
  
 解析程式和配接器提供者架構的主要優點是您可以藉由建立並註冊您自己自訂的解析程式，以解析端點資訊和設定的已註冊的 BizTalk 配接器的特定屬性的自訂配接器提供者擴充它。 如需詳細資訊，請參閱 <<c0> [ 修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。
