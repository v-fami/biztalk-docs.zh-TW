---
title: "WCF 訊息與協調流程中使用 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- WCF services, orchestrations
- WCF services, SOAP headers
ms.assetid: 31c01e35-a2a6-4ea9-bdf4-6d4311268dbe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7492ac6e1f8e43559fa921f9ddd3b60d644fe5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-orchestrations"></a><span data-ttu-id="36c72-102">在協調流程使用 WCF 訊息中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="36c72-102">Using SOAP Headers in WCF Messages with Orchestrations</span></span>
<span data-ttu-id="36c72-103">若要傳送外寄 WCF 訊息自訂 SOAP 標頭在協調流程中，您可以使用內容屬性， **WCF。OutboundCustomHeaders**。</span><span class="sxs-lookup"><span data-stu-id="36c72-103">To send the custom SOAP headers with outgoing WCF messages in orchestrations, you use the context property, **WCF.OutboundCustomHeaders**.</span></span> <span data-ttu-id="36c72-104">WCF 配接器傳送自訂 SOAP 標頭結合的標準 SOAP 標頭，WCF 基礎結構會使用適用於 Web 服務標準，例如 Ws-addressing、 Ws-security 和 Ws-atomictransaction。</span><span class="sxs-lookup"><span data-stu-id="36c72-104">The WCF adapters send the custom SOAP headers combined with the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="36c72-105">當您使用**OutboundCustomHeaders**屬性，屬性必須有\<**標頭**> 元素是根項目。</span><span class="sxs-lookup"><span data-stu-id="36c72-105">When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**> element as the root element.</span></span> <span data-ttu-id="36c72-106">所有自訂 SOAP 標頭必須置於\<**標頭**> 項目。</span><span class="sxs-lookup"><span data-stu-id="36c72-106">All of the custom SOAP headers must be placed inside the \<**headers**> element.</span></span> <span data-ttu-id="36c72-107">如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**>\</**標頭**> 或\< **標頭**/ > 若要**OutboundCustomHeaders**屬性。</span><span class="sxs-lookup"><span data-stu-id="36c72-107">If the custom SOAP header value is an empty string, you must assign \<**headers**>\</**headers**> or \<**headers**/> to the **OutboundCustomHeaders** property.</span></span>  
  
 <span data-ttu-id="36c72-108">針對協調流程，SOAP 標頭內容屬性會設為包含 XML 資料的字串。</span><span class="sxs-lookup"><span data-stu-id="36c72-108">For orchestrations, the SOAP header context properties are set to strings that contain XML data.</span></span> <span data-ttu-id="36c72-109">使用 BizTalk 運算式編輯器 中設定這些字串**訊息指派**或**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="36c72-109">You set these strings by using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span> <span data-ttu-id="36c72-110">如需如何搭配 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭搭配 WCF 配接器，從[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。</span><span class="sxs-lookup"><span data-stu-id="36c72-110">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
 <span data-ttu-id="36c72-111">下列範例 (擷取自「訊息指派」或「運算式」圖形) 說明設定內容屬性的字串：</span><span class="sxs-lookup"><span data-stu-id="36c72-111">The following example (from a Message Assignment or an Expression shape) shows the string setting the context property:</span></span>  
  
```  
outboundMessageInstance(WCF.OutboundCustomHeaders) = "<headers><Origination>Home</Origination><Destination>Work</Destination></headers>"  
```  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a><span data-ttu-id="36c72-112">建立 XmlDocument 來設定內容屬性</span><span class="sxs-lookup"><span data-stu-id="36c72-112">Creating an XmlDocument to set context properties</span></span>  
 <span data-ttu-id="36c72-113">您可以設定**WCF。OutboundCustomHeaders**內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="36c72-113">You can set the **WCF.OutboundCustomHeaders** context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span> <span data-ttu-id="36c72-114">宣告類型的變數**XMLDocument**並指派 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="36c72-114">You declare a variable of type **XMLDocument** and assign the XML data.</span></span>  
  
 <span data-ttu-id="36c72-115">下列範例說明如何宣告類型的變數**XMLDocument**並指派 XML 資料：</span><span class="sxs-lookup"><span data-stu-id="36c72-115">The following example shows declaring a variable of type **XMLDocument** and assigning the XML data:</span></span>  
  
```  
xmlDoc.LoadXml("<headers><Origination>Home</Origination><Destination>Work</Destination></headers>");  
```  
  
 <span data-ttu-id="36c72-116">下列範例說明如何設定內容屬性：</span><span class="sxs-lookup"><span data-stu-id="36c72-116">The following example shows setting the context property:</span></span>  
  
```  
RequestMessageInstance(WCF.OutboundCustomHeaders) = xmlDoc.OuterXml;  
```  
  
 <span data-ttu-id="36c72-117">如需有關如何使用 BizTalk 運算式編輯器的詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="36c72-117">For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span> <span data-ttu-id="36c72-118">如需有關呼叫[!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)]類別，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="36c72-118">For more information about calling [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c72-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36c72-119">See Also</span></span>  
 <span data-ttu-id="36c72-120">[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="36c72-120">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 <span data-ttu-id="36c72-121">[SOAP 標頭與使用的 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="36c72-121">[SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md) </span></span>  
 [<span data-ttu-id="36c72-122">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="36c72-122">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)