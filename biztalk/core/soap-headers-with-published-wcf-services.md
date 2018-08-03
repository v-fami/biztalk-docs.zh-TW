---
title: SOAP 標頭與已發佈的 WCF 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing, SOAP headers [WCF services]
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: 5564a57e-e241-4595-a959-4289c8502410
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea48ab7afeae2b54136c9134d3ef92878b802924
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985367"
---
# <a name="soap-headers-with-published-wcf-services"></a><span data-ttu-id="49804-102">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="49804-102">SOAP Headers with Published WCF Services</span></span>
<span data-ttu-id="49804-103">WCF 接收配接器可以將所有的 SOAP 標頭值複製到輸入訊息中**InboundHeaders**屬性，或者可以寫入或升級至 BizTalk 訊息內容的指定的值。</span><span class="sxs-lookup"><span data-stu-id="49804-103">The WCF receive adapters can copy all the SOAP header values in the inbound messages to the **InboundHeaders** property, or they can write or promote specified values to the BizTalk message context.</span></span> <span data-ttu-id="49804-104">配接器可以處理自訂 SOAP 標頭和 WCF 基礎結構使用的標準 SOAP 標頭，例如 WS-Addressing、WS-Security 和 WS-AtomicTransaction。</span><span class="sxs-lookup"><span data-stu-id="49804-104">The adapters can work with both custom SOAP headers and standard SOAP headers that the WCF infrastructure uses, such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="49804-105">**InboundHeaders**內容屬性位於目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**，並包含的內送訊息中的 SOAP 標頭值的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="49804-105">The **InboundHeaders** context property is in the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**, and contains string representations of the SOAP header values in inbound messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49804-106">如果您要升級指定的 SOAP 標頭值，則 BizTalk 專案中必須有已部署的屬性結構描述，與您要升級的值相對應。</span><span class="sxs-lookup"><span data-stu-id="49804-106">If you are going to promote the SOAP header values you specified, there must be a deployed property schema in your BizTalk project that corresponds to the values you are promoting.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49804-107">升級的屬性不能超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="49804-107">The promoted properties cannot be longer than 256 characters.</span></span>  
  
 <span data-ttu-id="49804-108">下列 XML 資料顯示的 SOAP 標頭的字串表示法的範例**InboundHeaders**屬性。</span><span class="sxs-lookup"><span data-stu-id="49804-108">The following XML data shows an example of the string representation of the SOAP headers for the **InboundHeaders** property.</span></span> <span data-ttu-id="49804-109">此資料來自用戶端，並且會傳送至 BizTalk 接收位置。</span><span class="sxs-lookup"><span data-stu-id="49804-109">This comes from the client and is sent to the BizTalk receive location.</span></span>  
  
```  
<headers>  
<a:Action s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">Operation_1</a:Action>  
<SalesAgent xmlns="Microsoft.Samples.BizTalk.WCF.CustomSoapHeaderPipeline">Contoso</SalesAgent>  
<a:MessageID xmlns:a="http://www.w3.org/2005/08/addressing">urn:uuid:26e6720f-5a82-4ef2-b597-6ef077bab92e</a:MessageID>  
<a:ReplyTo xmlns:a="http://www.w3.org/2005/08/addressing"><a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address></a:ReplyTo>  
<a:To s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">net.tcp://localhost:9990/NetTcpOrderProcess</a:To>  
</headers>  
```  
  
 <span data-ttu-id="49804-110">若要將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容，您必須將包含屬性名稱和命名空間的值配對集合放入 WCF 訊息，讓 WCF 配接器能夠辨識將寫入或升級的標頭值。</span><span class="sxs-lookup"><span data-stu-id="49804-110">To write or promote SOAP header values to the BizTalk message context, you need to put a collection of value pairs that consist of property name and namespace into the WCF message so that the WCF adapters will recognize that the header values are to be written or promoted.</span></span> <span data-ttu-id="49804-111">WCF 訊息必須包含下列訊息屬性，WCF 配接器才能將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：</span><span class="sxs-lookup"><span data-stu-id="49804-111">A WCF adapter expects the following message properties in the WCF messages for writing or promoting SOAP header values to the BizTalk message context:</span></span>  
  
- <span data-ttu-id="49804-112">若要升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器會尋找金鑰組**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote**和值**清單\<KeyValuePair\<XmlQualifiedName，物件\>\>**.</span><span class="sxs-lookup"><span data-stu-id="49804-112">To promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.</span></span>  
  
   <span data-ttu-id="49804-113">使用此配對，WCF 配接器需要命名空間、 名稱和值**XmlQualifiedName**物件，並將它們用於升級的標頭值。</span><span class="sxs-lookup"><span data-stu-id="49804-113">Using this pair, WCF adapters take the namespace, name, and value from the **XmlQualifiedName** object and use them for promoting the header values.</span></span>  
  
- <span data-ttu-id="49804-114">若要撰寫，但不是升級至 BizTalk 訊息內容的 SOAP 標頭值，WCF 配接器所需的金鑰組**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext**和 值**清單\<KeyValuePair\<XmlQualifiedName，物件\>\>**。</span><span class="sxs-lookup"><span data-stu-id="49804-114">To write but not promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.</span></span>  
  
   <span data-ttu-id="49804-115">使用此配對，WCF 配接器便可將值寫入訊息內容。</span><span class="sxs-lookup"><span data-stu-id="49804-115">Using this pair, WCF adapters write the values to the message context.</span></span>  
  
  <span data-ttu-id="49804-116">下列程式碼顯示如何將 SOAP 標頭值寫入或升級至 BizTalk 訊息內容：</span><span class="sxs-lookup"><span data-stu-id="49804-116">The following code shows how to write or promote the SOAP header values to the BizTalk message context:</span></span>  
  
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
  
 <span data-ttu-id="49804-117">「BizTalk WCF 服務發佈精靈」不會將自訂 SOAP 標頭定義包含在產生的中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="49804-117">The BizTalk WCF Service Publishing Wizard does not include custom SOAP header definitions in the generated metadata.</span></span> <span data-ttu-id="49804-118">若要使用自訂 SOAP 標頭發佈 WCF 服務的中繼資料，您應手動建立「Web 服務描述語言」(WSDL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="49804-118">To publish metadata for WCF services using custom SOAP headers, you should manually create a Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="49804-119">您可以使用**externalMetadataLocation**屬性[ \<serviceMetadata\> ](http://go.microsoft.com/fwlink/?LinkId=89121) Web.config 檔案，精靈會產生指定的位置中的項目WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="49804-119">You can use the **externalMetadataLocation** attribute of the [\<serviceMetadata\>](http://go.microsoft.com/fwlink/?LinkId=89121) element in the Web.config file that the wizard generates to specify the location of the WSDL file.</span></span> <span data-ttu-id="49804-120">WSDL 檔案會傳回給使用者，以回應 WSDL 和中繼資料交換 (MEX) 要求，而不是自動產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="49804-120">The WSDL file is returned to the user in response to WSDL and metadata exchange (MEX) requests instead of the auto-generated WSDL.</span></span>  
  
 <span data-ttu-id="49804-121">下列 XML 資料顯示定義自訂 SOAP 標頭之 WSDL 檔案一部分的範例：</span><span class="sxs-lookup"><span data-stu-id="49804-121">The following XML data shows an example of a part of the WSDL file defining custom SOAP headers:</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="49804-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="49804-122">In This Section</span></span>  
  
-   [<span data-ttu-id="49804-123">使用協調流程存取 WCF 訊息中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="49804-123">Accessing SOAP Headers in WCF Messages with Orchestrations</span></span>](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [<span data-ttu-id="49804-124">使用管線元件存取 WCF 訊息中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="49804-124">Accessing SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a><span data-ttu-id="49804-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49804-125">See Also</span></span>  
 <span data-ttu-id="49804-126">[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="49804-126">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="49804-127">SOAP 標頭與使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="49804-127">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)