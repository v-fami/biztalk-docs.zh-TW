---
title: 叫用商務服務方法使用整合物件使用 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- integration objects
- how to, invoke business service methods with integration objects
- business service methods, invoking with integration objects
ms.assetid: ac0fa80a-3451-436e-8a1a-b6b5e93081e7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132c269d347f67cbad3038bcbbb8e62d29112b6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962844"
---
# <a name="invoke-business-service-methods-with-integration-objects-using-the-siebel-adapter"></a><span data-ttu-id="3c5cc-102">叫用商務服務方法使用整合物件使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="3c5cc-102">Invoke Business Service Methods with Integration Objects using the Siebel adapter</span></span>
<span data-ttu-id="3c5cc-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端叫用商務服務方法使用整合物件。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to invoke business service methods that work with integration objects.</span></span> <span data-ttu-id="3c5cc-104">這些商務服務通常有 IN、 OUT 或 IN OUT 參數的 「 階層 」 資料類型變更為傳送或接收整合物件資料。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-104">These business services typically have IN, OUT, or IN OUT parameters of "hierarchy" data type to send or receive integration object data.</span></span>  
  
 <span data-ttu-id="3c5cc-105">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開 （expose) 這些階層的類型為字串。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-105">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes these hierarchical types as strings.</span></span> <span data-ttu-id="3c5cc-106">這些字串值是基本上是封裝在 XML CDATA 區段的 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-106">These string values are essentially an XML string encapsulated in an XML CDATA section.</span></span> <span data-ttu-id="3c5cc-107">XML 字串是與配接器用戶端會嘗試傳送或接收的整合物件的 XML 結構描述相容。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-107">The XML string is compatible with the XML schema of the integration object the adapter client is trying to send or receive.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="3c5cc-108">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="3c5cc-108">Sample Based On This Topic</span></span>  
 <span data-ttu-id="3c5cc-109">基礎的範例，SiebelAdapterIntegrationObjects，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-109">A sample, SiebelAdapterIntegrationObjects, based on this topic is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3c5cc-110">如需詳細資訊，請參閱[Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-110">For more information, see [Samples for the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).</span></span>
  
## <a name="creating-an-orchestration-to-invoke-business-service-methods-with-integration-objects"></a><span data-ttu-id="3c5cc-111">建立協調流程叫用商務服務方法使用整合物件</span><span class="sxs-lookup"><span data-stu-id="3c5cc-111">Creating an Orchestration to Invoke Business Service Methods with Integration Objects</span></span>  
 <span data-ttu-id="3c5cc-112">建立協調流程叫用商務服務方法使用整合物件參數類似於叫用其他商務服務的協調流程中所述[叫用商務服務方法使用 BizTalk Server 和Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-112">Creating an orchestration to invoke a business service method that takes integration object parameters is similar to the orchestration to invoke any other business service, as described in [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span></span>  
  
 <span data-ttu-id="3c5cc-113">差異在於您卸除的協調流程的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-113">The difference lies in the request message that you drop for the orchestration.</span></span> <span data-ttu-id="3c5cc-114">這項差異是由於下列原因：</span><span class="sxs-lookup"><span data-stu-id="3c5cc-114">This difference is because of the following:</span></span>  
  
-   <span data-ttu-id="3c5cc-115">要求訊息的結構描述是不同的因為叫用不同的商務服務。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-115">The schema for the request message is different because you invoke a different business service.</span></span>  
  
-   <span data-ttu-id="3c5cc-116">要求訊息包含整合物件的 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-116">The request message contains the XML string for the integration object.</span></span> <span data-ttu-id="3c5cc-117">這段 XML 會封裝在 CDATA 區段。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-117">This XML is encapsulated in a CDATA section.</span></span> <span data-ttu-id="3c5cc-118">您必須先產生整合物件的結構描述，然後再建立符合結構描述的 XML。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-118">You must first generate the schema for the integration object and then create an XML that conforms to the schema.</span></span> <span data-ttu-id="3c5cc-119">這段 XML 必須傳遞至配接器傳送要求訊息的 CDATA 區段內。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-119">This XML must be passed within the CDATA section of the request message sent to the adapter.</span></span>  
  
 <span data-ttu-id="3c5cc-120">產生的 XML，符合整合物件結構描述，而且包含在要求訊息後，您必須在檔案位置，就像任何其他協調流程的卸除要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-120">After you have generated the XML that conforms to the integration object schema and included it in the request message, you must drop the request message at a FILE location, just like you do for any other orchestration.</span></span> <span data-ttu-id="3c5cc-121">尋找其他檔案位置中的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-121">Look for the response message in the other FILE location.</span></span>  
  
## <a name="request-and-response-messages-for-invoking-business-service-with-integration-objects"></a><span data-ttu-id="3c5cc-122">要求和回應訊息，來叫用商務服務，使用整合物件</span><span class="sxs-lookup"><span data-stu-id="3c5cc-122">Request and Response Messages for Invoking Business Service with Integration Objects</span></span>  
 <span data-ttu-id="3c5cc-123">如前所述，叫用商務服務採用整合物件參數的唯一差異是傳送至配接器的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-123">As mentioned before, the only difference for invoking a business service that takes integration object parameters is the request message sent to the adapter.</span></span> <span data-ttu-id="3c5cc-124">本節提供建立要求訊息時，您必須執行的步驟的指示。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-124">This section provides instructions on the steps you must perform to create the request message.</span></span>  
  
 <span data-ttu-id="3c5cc-125">進一步了解，採取的 Siebel 商務服務 「 EAI Siebel 配接器 」 做為範例。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-125">For better understanding, take a Siebel business service 'EAI Siebel Adapter' as an example.</span></span> <span data-ttu-id="3c5cc-126">「 EAI Siebel 配接器 」 商務服務會依據 Siebel 整合物件，而 「 範例帳戶 」。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-126">The 'EAI Siebel Adapter' business service operates on a Siebel integration object, 'Sample Account'.</span></span> <span data-ttu-id="3c5cc-127">您必須執行下列工作來建立要求訊息來叫用 「 EAI Siebel 配接器 」 商務服務所公開的方法：</span><span class="sxs-lookup"><span data-stu-id="3c5cc-127">You must perform the following tasks to create the request message to invoke a method exposed by the 'EAI Siebel Adapter' business service:</span></span>  
  
-   <span data-ttu-id="3c5cc-128">**產生結構描述的 EAI Siebel 配接器商務服務**。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-128">**Generate the schema for the EAI Siebel Adapter business service**.</span></span> <span data-ttu-id="3c5cc-129">您必須使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-129">You must use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema.</span></span> <span data-ttu-id="3c5cc-130">當您產生結構描述時，會產生符合結構描述的 XML。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-130">Once you generate the schema, generate the XML that conforms to the schema.</span></span>  
  
-   <span data-ttu-id="3c5cc-131">**產生整合物件的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-131">**Generate the schema for the integration object**.</span></span> <span data-ttu-id="3c5cc-132">使用 Siebel 工具來產生結構描述的整合物件。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-132">Use Siebel Tools to generate schema for an integration object.</span></span> <span data-ttu-id="3c5cc-133">從 Siebel 工具介面中，選取 整合物件，例如，範例帳戶，然後按一下**產生結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-133">From the Siebel Tools interface, select the integration object, for example, Sample Account, and click **Generate Schema**.</span></span> <span data-ttu-id="3c5cc-134">在產生結構描述時，請確定：</span><span class="sxs-lookup"><span data-stu-id="3c5cc-134">While generating the schema, make sure:</span></span>  
  
    -   <span data-ttu-id="3c5cc-135">**從清單中選取商務服務**下拉式清單具有 「 EAI XML XSD 產生器 」 的值。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-135">The **Select a Business Service from the list** drop-down has the value "EAI XML XSD Generator".</span></span>  
  
    -   <span data-ttu-id="3c5cc-136">**從清單中選取信封類型**下拉式清單具有 「 Siebel 訊息信封 」 的值。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-136">The **Select an envelope type from the list** drop-down has the value "Siebel Message Envelope".</span></span>  
  
     <span data-ttu-id="3c5cc-137">如需詳細資訊，請參閱 Siebel 文件。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-137">For more information, see the Siebel documentation.</span></span>  
  
-   <span data-ttu-id="3c5cc-138">**建立 XML 訊息，並整合物件的結構描述符合**。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-138">**Create an XML message that conforms to schema of the integration object**.</span></span> <span data-ttu-id="3c5cc-139">針對 「 範例帳戶 」 整合物件產生範例 XML 訊息看起來像：</span><span class="sxs-lookup"><span data-stu-id="3c5cc-139">A sample XML message generated for the 'Sample Account' integration object looks like:</span></span>  
  
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
  
-   <span data-ttu-id="3c5cc-140">**將這個 XML 訊息傳遞做為商務服務方法的要求訊息中的 CDATA 項目值**。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-140">**Pass this XML message as the value for the CDATA element in the request message for the business service method**.</span></span> <span data-ttu-id="3c5cc-141">範例要求訊息，其中包含上述 XML 訊息中的 CDATA 項目看起來如下。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-141">A sample request message that contains the preceding XML message within a CDATA element looks like the following.</span></span> <span data-ttu-id="3c5cc-142">此範例要求是叫用 「 EAI Siebel 配接器 」 商務服務的插入方法。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-142">This sample request is to invoke the Insert method for the 'EAI Siebel Adapter' business service.</span></span>  
  
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
  
     <span data-ttu-id="3c5cc-143">上述的要求訊息的回應從 Siebel 如下所示：</span><span class="sxs-lookup"><span data-stu-id="3c5cc-143">The response from Siebel for the above request message resembles the following:</span></span>  
  
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
  
 <span data-ttu-id="3c5cc-144">使用 BizTalk 功能，配接器用戶端也可以執行其他驗證整合物件 IN 和 OUT 參數針對整合物件結構描述 （取自 Siebel 工具）。</span><span class="sxs-lookup"><span data-stu-id="3c5cc-144">Using BizTalk features, adapter clients can also perform additional validation of the integration object IN and OUT parameter against the integration object schema (obtained from Siebel Tools.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5cc-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c5cc-145">See Also</span></span>  
<span data-ttu-id="3c5cc-146">[開發 BizTalk 應用程式使用 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)  </span><span class="sxs-lookup"><span data-stu-id="3c5cc-146">[Develop BizTalk Applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)  </span></span>  
[<span data-ttu-id="3c5cc-147">開發您的 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="3c5cc-147">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)