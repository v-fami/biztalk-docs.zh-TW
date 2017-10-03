---
title: "SOAP 標頭與已發佈的 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, SOAP headers [WCF services]
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: 5564a57e-e241-4595-a959-4289c8502410
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b62ebea1380e686a0afbf18dc63aedbfab190fac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-headers-with-published-wcf-services"></a>SOAP 標頭與已發佈的 WCF 服務
WCF 接收配接器可以將所有 SOAP 標頭值都複製到輸入訊息中**InboundHeaders**屬性，或者可以寫入或升級至 BizTalk 訊息內容的指定的值。 配接器可以處理自訂 SOAP 標頭和 WCF 基礎結構使用的標準 SOAP 標頭，例如 WS-Addressing、WS-Security 和 WS-AtomicTransaction。 **InboundHeaders**內容屬性位於目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**，並包含的 soap 的字串表示法內送訊息中的標頭值。  
  
> [!NOTE]
>  如果您要升級指定的 SOAP 標頭值，則 BizTalk 專案中必須有已部署的屬性結構描述，與您要升級的值相對應。  
  
> [!NOTE]
>  升級的屬性不能超過 256 個字元。  
  
 下列 XML 資料顯示的 SOAP 標頭的字串表示法範例**InboundHeaders**屬性。 此資料來自用戶端，並且會傳送至 BizTalk 接收位置。  
  
```  
<headers>  
<a:Action s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">Operation_1</a:Action>  
<SalesAgent xmlns="Microsoft.Samples.BizTalk.WCF.CustomSoapHeaderPipeline">Contoso</SalesAgent>  
<a:MessageID xmlns:a="http://www.w3.org/2005/08/addressing">urn:uuid:26e6720f-5a82-4ef2-b597-6ef077bab92e</a:MessageID>  
<a:ReplyTo xmlns:a="http://www.w3.org/2005/08/addressing"><a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address></a:ReplyTo>  
<a:To s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">net.tcp://localhost:9990/NetTcpOrderProcess</a:To>  
</headers>  
```  
  
 若要將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容，您必須將包含屬性名稱和命名空間的值配對集合放入 WCF 訊息，讓 WCF 配接器能夠辨識將寫入或升級的標頭值。 WCF 訊息必須包含下列訊息屬性，WCF 配接器才能將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：  
  
-   若要升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器會尋找的索引鍵配對**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote**和值**清單 <KeyValuePair\<XmlQualifiedName，物件 >>**。  
  
     使用此配對，WCF 配接器需要命名空間、 名稱和值從**XmlQualifiedName**物件，並使用它們來升級標頭值。  
  
-   若要撰寫，但未升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器會尋找的索引鍵配對**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext**和值**清單 < KeyValuePair\<XmlQualifiedName，物件 >>**。  
  
     使用此配對，WCF 配接器便可將值寫入訊息內容。  
  
 下列程式碼顯示如何將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：  
  
```  
const string PropertiesToPromoteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote";  
const string PropertiesToWriteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext";  
  
XmlQualifiedName PropName1=new XmlQualifiedName("Destination", "http://tempuri.org/2007/sample-properties");  
XmlQualifiedName PropName2=new XmlQualifiedName("Source", "http://tempuri.org/2007/sample-properties");  
  
//Create a List of KeyValuePairs that indicate properties to be promoted to BizTalk message context.   
//A Property Schema must be deployed and string values have a limit of 256 characters  
List<KeyValuePair<XmlQualifiedName, object>> promoteProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
promoteProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName1, "Property value"));  
wcfMessage.Properties[PropertiesToPromoteKey]=promoteProps;  
  
//Create a List of KeyValuePairs that indicate properties to be written to BizTalk message context  
List<KeyValuePair<XmlQualifiedName, object>> writeProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
writeProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName2, "Property value"));  
wcfMessage.Properties[PropertiesToWriteKey]=writeProps;  
```  
  
 「BizTalk WCF 服務發佈精靈」不會將自訂 SOAP 標頭定義包含在產生的中繼資料內。 若要使用自訂 SOAP 標頭發佈 WCF 服務的中繼資料，您應手動建立「Web 服務描述語言」(WSDL) 檔案。 您可以使用**externalMetadataLocation**屬性[ \<serviceMetadata >](http://go.microsoft.com/fwlink/?LinkId=89121)精靈會產生指定的 WSDL 檔案的位置在 Web.config 檔案中的項目。 WSDL 檔案會傳回給使用者，以回應 WSDL 和中繼資料交換 (MEX) 要求，而不是自動產生的 WSDL。  
  
 下列 XML 資料顯示定義自訂 SOAP 標頭之 WSDL 檔案一部分的範例：  
  
```  
<wsdl:operation name="Request">  
  <soap12:operation soapAction="http://Microsoft.Samples.BizTalk.NetTcpAdapter/OrderProcess/IOrderProcess/Request" style="document" />   
   <wsdl:input name="Order">  
     <soap12:header message="i0:Order_Headers" part="SalesAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:input>  
   <wsdl:output name="OrderConfirmation">  
     <soap12:header message="i0:OrderConfirmation_Headers" part="PaymentAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:output>  
</wsdl:operation>  
```  
  
## <a name="in-this-section"></a>本節內容  
  
-   [存取 WCF 訊息與協調流程中的 SOAP 標頭](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [存取 WCF 訊息的管線元件中的 SOAP 標頭](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與使用的 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md)