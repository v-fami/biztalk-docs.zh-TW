---
title: "叫用商務服務方法使用整合物件使用 Siebel 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- integration objects
- how to, invoke business service methods with integration objects
- business service methods, invoking with integration objects
ms.assetid: ac0fa80a-3451-436e-8a1a-b6b5e93081e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132c269d347f67cbad3038bcbbb8e62d29112b6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-business-service-methods-with-integration-objects-using-the-siebel-adapter"></a>叫用商務服務方法使用整合物件使用 Siebel 配接器
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端叫用商務服務方法使用整合物件。 這些商務服務通常有 IN、 OUT 或 IN OUT 參數的 「 階層 」 資料類型變更為傳送或接收整合物件資料。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開 （expose) 這些階層的類型為字串。 這些字串值是基本上是封裝在 XML CDATA 區段的 XML 字串。 XML 字串是與配接器用戶端會嘗試傳送或接收的整合物件的 XML 結構描述相容。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，SiebelAdapterIntegrationObjects，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。
  
## <a name="creating-an-orchestration-to-invoke-business-service-methods-with-integration-objects"></a>建立協調流程叫用商務服務方法使用整合物件  
 建立協調流程叫用商務服務方法使用整合物件參數類似於叫用其他商務服務的協調流程中所述[叫用商務服務方法使用 BizTalk Server 和Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。  
  
 差異在於您卸除的協調流程的要求訊息。 這項差異是由於下列原因：  
  
-   要求訊息的結構描述是不同的因為叫用不同的商務服務。  
  
-   要求訊息包含整合物件的 XML 字串。 這段 XML 會封裝在 CDATA 區段。 您必須先產生整合物件的結構描述，然後再建立符合結構描述的 XML。 這段 XML 必須傳遞至配接器傳送要求訊息的 CDATA 區段內。  
  
 產生的 XML，符合整合物件結構描述，而且包含在要求訊息後，您必須在檔案位置，就像任何其他協調流程的卸除要求訊息。 尋找其他檔案位置中的回應訊息。  
  
## <a name="request-and-response-messages-for-invoking-business-service-with-integration-objects"></a>要求和回應訊息，來叫用商務服務，使用整合物件  
 如前所述，叫用商務服務採用整合物件參數的唯一差異是傳送至配接器的要求訊息。 本節提供建立要求訊息時，您必須執行的步驟的指示。  
  
 進一步了解，採取的 Siebel 商務服務 「 EAI Siebel 配接器 」 做為範例。 「 EAI Siebel 配接器 」 商務服務會依據 Siebel 整合物件，而 「 範例帳戶 」。 您必須執行下列工作來建立要求訊息來叫用 「 EAI Siebel 配接器 」 商務服務所公開的方法：  
  
-   **產生結構描述的 EAI Siebel 配接器商務服務**。 您必須使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 當您產生結構描述時，會產生符合結構描述的 XML。  
  
-   **產生整合物件的結構描述**。 使用 Siebel 工具來產生結構描述的整合物件。 從 Siebel 工具介面中，選取 整合物件，例如，範例帳戶，然後按一下**產生結構描述**。 在產生結構描述時，請確定：  
  
    -   **從清單中選取商務服務**下拉式清單具有 「 EAI XML XSD 產生器 」 的值。  
  
    -   **從清單中選取信封類型**下拉式清單具有 「 Siebel 訊息信封 」 的值。  
  
     如需詳細資訊，請參閱 Siebel 文件。  
  
-   **建立 XML 訊息，並整合物件的結構描述符合**。 針對 「 範例帳戶 」 整合物件產生範例 XML 訊息看起來像：  
  
    ```  
    <?xml version="1.0" encoding="UTF-16"?>  
    <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
      <ListOfSampleAccount>  
        <Account>  
          <CurrencyCode>USD</CurrencyCode>  
          <Location>Redmond</Location>  
          <Name>IntegrationObjectTest</Name>  
        </Account>  
      </ListOfSampleAccount>  
    </SiebelMessage>  
    ```  
  
-   **將這個 XML 訊息傳遞做為商務服務方法的要求訊息中的 CDATA 項目值**。 範例要求訊息，其中包含上述 XML 訊息中的 CDATA 項目看起來如下。 此範例要求是叫用 「 EAI Siebel 配接器 」 商務服務的插入方法。  
  
    ```  
    <Insert xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertRequestRecord />   
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </Insert>  
    ```  
  
     上述的要求訊息的回應從 Siebel 如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <InsertResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertResult>  
        <ErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">0x0</ErrorCode>   
        <ErrorContextIntComp xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorContextSearchSpec xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <PrimaryRowId xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">1-6SPSJ</PrimaryRowId>   
      </InsertResult>  
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </InsertResponse>  
    ```  
  
 使用 BizTalk 功能，配接器用戶端也可以執行其他驗證整合物件 IN 和 OUT 參數針對整合物件結構描述 （取自 Siebel 工具）。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式使用 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)    
[開發您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)