---
title: "存取 WCF 訊息與協調流程中的 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- orchestrations, WCF services
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: fe02fb02-18d6-4fc6-89e0-b06bdbfa5cb4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bfd1dd4e09071c3d7bcccf28878f19e13acad8a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-soap-headers-in-wcf-messages-with-orchestrations"></a><span data-ttu-id="71371-102">使用協調流程存取 WCF 訊息中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="71371-102">Accessing SOAP Headers in WCF Messages with Orchestrations</span></span>
<span data-ttu-id="71371-103">若要存取的協調流程中的內送 WCF 訊息的 SOAP 標頭值，您可以使用內容屬性**WCF。InboundHeaders**。</span><span class="sxs-lookup"><span data-stu-id="71371-103">To access the SOAP header values of incoming WCF messages in orchestrations, you use the context property **WCF.InboundHeaders**.</span></span> <span data-ttu-id="71371-104">WCF 配接器複製到輸入訊息中的自訂 SOAP 標頭和標準 SOAP 標頭**WCF。InboundHeaders**屬性。</span><span class="sxs-lookup"><span data-stu-id="71371-104">The WCF adapters copy custom SOAP headers and standard SOAP headers in the inbound messages to the **WCF.InboundHeaders** property.</span></span> <span data-ttu-id="71371-105">您也可以使用 WCF 配接器，選取要以程式設計方式升級至或寫入至內容屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="71371-105">The WCF adapters also allow you to select the properties you would like to promote or write to the context properties programmatically.</span></span> <span data-ttu-id="71371-106">請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="71371-106">See [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md) for more details.</span></span>  
  
 <span data-ttu-id="71371-107">內容屬性中所包含的值是包含 XML 資料字串\<**標頭**\>根項目，並傳入的 SOAP 標頭複製成為子項目的\< **標頭**\>項目。</span><span class="sxs-lookup"><span data-stu-id="71371-107">The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element.</span></span> <span data-ttu-id="71371-108">若要存取此資料最簡單的方式是使用 BizTalk 運算式編輯器，在**訊息指派**或**運算式**圖形中，將字串載入**XmlDocument**，並使用若要存取特定欄位的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="71371-108">The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape, load the string in an **XmlDocument**, and use XPath queries to access specific fields.</span></span> <span data-ttu-id="71371-109">如需在 BizTalk 運算式編輯器 」 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。</span><span class="sxs-lookup"><span data-stu-id="71371-109">For more information about creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
 <span data-ttu-id="71371-110">下列程式碼範例會取得要求 SOAP 標頭中**訊息指派**或**運算式**圖形**WCF。InboundHeaders**屬性：</span><span class="sxs-lookup"><span data-stu-id="71371-110">The following code example gets the request SOAP header in a **Message Assignment** or **Expression** shape for the **WCF.InboundHeaders** property:</span></span>  
  
```  
stringVar = inboundMessageInstance(WCF.InboundHeaders);  
```  
  
 <span data-ttu-id="71371-111">內容屬性與特定的訊息有關聯。</span><span class="sxs-lookup"><span data-stu-id="71371-111">Context properties are associated with a particular message.</span></span> <span data-ttu-id="71371-112">「傳訊引擎」不會將要求訊息中 SOAP 標頭的值自動對應至回應訊息。</span><span class="sxs-lookup"><span data-stu-id="71371-112">The Messaging Engine does not automatically map the values of the SOAP headers from the request message to the response message.</span></span> <span data-ttu-id="71371-113">在建立 WCF 服務的回應訊息時，您必須特別設定 SOAP 標頭值，透過**WCF。OutboundCustomHeaders**屬性。</span><span class="sxs-lookup"><span data-stu-id="71371-113">When creating the response message for a WCF service, you must specifically set the SOAP header values through the **WCF.OutboundCustomHeaders** property.</span></span> <span data-ttu-id="71371-114">下列命令是設定 SOAP 標頭內容屬性的最簡單的方法：</span><span class="sxs-lookup"><span data-stu-id="71371-114">The following command is the simplest method of setting a SOAP header context property:</span></span>  
  
```  
outboundMessageInstance(WCF.OutbounCustomHeaders) = "<headers><Origination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Home</Origination><Destination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Work</Destination></headers>"  
```  
  
 <span data-ttu-id="71371-115">您也可以設定內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="71371-115">You can also set the context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span>  
  
 <span data-ttu-id="71371-116">使用 WCF 配接器存取 SOAP 標頭如何的相關資訊，請參閱 SDK 範例 「 使用自訂 SOAP 標頭與 WCF 配接器 >，網址[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。</span><span class="sxs-lookup"><span data-stu-id="71371-116">For more information about how to access SOAP headers with the WCF adapters, see the SDK sample "Using Custom SOAP Headers with the WCF Adapters" at [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71371-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="71371-117">See Also</span></span>  
 <span data-ttu-id="71371-118">[存取 WCF 訊息的管線元件中的 SOAP 標頭](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="71371-118">[Accessing SOAP Headers in WCF Messages with Pipeline Components](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md) </span></span>  
 <span data-ttu-id="71371-119">[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="71371-119">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="71371-120">SOAP 標頭與使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="71371-120">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)