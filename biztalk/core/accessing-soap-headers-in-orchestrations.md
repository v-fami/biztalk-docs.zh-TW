---
title: "存取協調流程中的 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, properties
- orchestrations, SOAP headers
ms.assetid: 91fe053a-3f16-497c-b4bb-5fb54bec62e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 516b2bcc57bef507a028f30c61fd329a5fd7a598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-orchestrations"></a><span data-ttu-id="88f27-102">在協調流程中存取 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="88f27-102">Accessing SOAP Headers in Orchestrations</span></span>
<span data-ttu-id="88f27-103">您可以在協調流程中，存取定義和未知之 SOAP 標頭的 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="88f27-103">You can access the SOAP header context properties in orchestrations for defined and unknown SOAP headers.</span></span> <span data-ttu-id="88f27-104">如需屬性結構描述和內容屬性的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="88f27-104">For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
## <a name="defined-soap-header-context-properties"></a><span data-ttu-id="88f27-105">已定義的 SOAP 標頭內容屬性</span><span class="sxs-lookup"><span data-stu-id="88f27-105">Defined SOAP header context properties</span></span>  
 <span data-ttu-id="88f27-106">在協調流程中定義的 SOAP 標頭內容屬性需要屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="88f27-106">The defined SOAP header context properties in orchestrations require a property schema.</span></span> <span data-ttu-id="88f27-107">屬性結構描述必須有目標命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**，而**Property Schema Base**屬性設定為**MessageContextPropertyBase**。</span><span class="sxs-lookup"><span data-stu-id="88f27-107">The property schema must have the target namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**, and the **Property Schema Base** property set to **MessageContextPropertyBase**.</span></span> <span data-ttu-id="88f27-108">屬性結構描述中的每個根項目名稱必須符合定義的 SOAP 標頭的根項目名稱。</span><span class="sxs-lookup"><span data-stu-id="88f27-108">Each root element name in the property schema must match the root element name of the defined SOAP header.</span></span> <span data-ttu-id="88f27-109">然後，您可以存取使用的命名空間屬性結構描述和屬性名稱的內容屬性的值。</span><span class="sxs-lookup"><span data-stu-id="88f27-109">You can then access the values of the context properties using the namespace of the property schema and the property name.</span></span> <span data-ttu-id="88f27-110">屬性結構描述的命名空間會與上面所列的目標命名空間不同。</span><span class="sxs-lookup"><span data-stu-id="88f27-110">The namespace of the property schema is different from the target namespace listed above.</span></span> <span data-ttu-id="88f27-111">雖然屬性結構描述的命名空間可以是任何字串，則通常會預設為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="88f27-111">Although the namespace of the property schema can be any string, it usually defaults to the name of the project.</span></span>  
  
 <span data-ttu-id="88f27-112">下列範例將示範存取 SOAP 標頭內容屬性，屬性結構描述命名空間**SOAPHeader**，和屬性名稱**OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="88f27-112">The following example shows accessing the SOAP header context property for a property schema namespace, **SOAPHeader**, and the property name **OrigDest**:</span></span>  
  
```  
stringVar = requestMessageInstance(SOAPHeader.OrigDest);  
```  
  
> [!NOTE]
>  <span data-ttu-id="88f27-113">已定義的 SOAP 標題會視為 "in" 或 "out" 標頭。</span><span class="sxs-lookup"><span data-stu-id="88f27-113">Defined SOAP headers are treated either as "in" or "out" headers.</span></span> <span data-ttu-id="88f27-114">若精靈為要求和回應訊息定義相同的 SOAP 標頭，就不會自動在回應中傳回內送的值。</span><span class="sxs-lookup"><span data-stu-id="88f27-114">If the wizard defines the same SOAP header for the request and response message, the wizard does not automatically return the incoming value in the response.</span></span> <span data-ttu-id="88f27-115">您必須以明確的方式，將要求訊息的 SOAP 標頭內容屬性複製至回應訊息的 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="88f27-115">You must explicity copy the SOAP header context property of the request message to the SOAP header context property of the response message.</span></span>  
  
## <a name="copying-soap-header-context-property-of-incoming-message"></a><span data-ttu-id="88f27-116">複製內送訊息的 SOAP 標頭內容屬性</span><span class="sxs-lookup"><span data-stu-id="88f27-116">Copying SOAP header context property of incoming message</span></span>  
 <span data-ttu-id="88f27-117">您可將內送訊息的 SOAP 標頭內容屬性複製至回應訊息的同一個 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="88f27-117">You can copy the SOAP header context property of an incoming message to the same SOAP header context property of the response message.</span></span>  
  
 <span data-ttu-id="88f27-118">下列是複製 SOAP 標頭內容屬性的範例：</span><span class="sxs-lookup"><span data-stu-id="88f27-118">The following example shows copying the SOAP header context property:</span></span>  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = RequestMessageInstance(SOAPHeader.OrigDest);  
```  
  
 <span data-ttu-id="88f27-119">建立 SOAP 回應的 SOAP 標頭時，請確定是否正確地建立 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="88f27-119">When you create SOAP headers for the SOAP response, you ensure that you create your SOAP headers correctly.</span></span> <span data-ttu-id="88f27-120">SOAP 配接器不會驗證 SOAP 標頭內容屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="88f27-120">The SOAP adapter does not verify the contents of the SOAP header context properties.</span></span> <span data-ttu-id="88f27-121">若回應 SOAP 標頭的值不正確，SOAP 配接器便無法將回應訊息傳送給 Web 服務的取用者。</span><span class="sxs-lookup"><span data-stu-id="88f27-121">If the values of the response SOAP headers are incorrect, the SOAP adapter cannot send the response message to the consumer of your Web service.</span></span>  
  
## <a name="unknown-soap-header-context-property"></a><span data-ttu-id="88f27-122">未知的 SOAP 標頭內容屬性</span><span class="sxs-lookup"><span data-stu-id="88f27-122">Unknown SOAP header context property</span></span>  
 <span data-ttu-id="88f27-123">未知的 SOAP 標頭內容屬性不需要屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="88f27-123">The unknown SOAP header context property does not require a property schema.</span></span> <span data-ttu-id="88f27-124">您可以存取此全域內容屬性**SOAP。UnknownHeaders**。</span><span class="sxs-lookup"><span data-stu-id="88f27-124">You can access this global context property **SOAP.UnknownHeaders**.</span></span>  
  
 <span data-ttu-id="88f27-125">下列範例將示範存取未知的 SOAP 標頭內容屬性**SOAP。UnknownHeaders**:</span><span class="sxs-lookup"><span data-stu-id="88f27-125">The following example shows accessing the unknown SOAP header context property **SOAP.UnknownHeaders**:</span></span>  
  
```  
stringVar = RequestMessageInstance(SOAP.UnknownHeaders);  
```  
  
 <span data-ttu-id="88f27-126">內容屬性中包含的值是包含 XML 資料的字串。</span><span class="sxs-lookup"><span data-stu-id="88f27-126">The values contained in the context properties are strings containing XML data.</span></span> <span data-ttu-id="88f27-127">若要存取此資料最簡單的方式是使用 BizTalk 運算式編輯器，在**訊息指派**或**運算式**圖形，並將字串載入**XmlDocument**並使用若要存取特定欄位的 XPATH 查詢。</span><span class="sxs-lookup"><span data-stu-id="88f27-127">The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape and load the string in an **XmlDocument** and use XPATH queries to access specific fields.</span></span> <span data-ttu-id="88f27-128">在 BizTalk 運算式編輯器 」 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。</span><span class="sxs-lookup"><span data-stu-id="88f27-128">For more information creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
 <span data-ttu-id="88f27-129">內容屬性與特定的訊息有關聯。</span><span class="sxs-lookup"><span data-stu-id="88f27-129">Context properties are associated with a particular message.</span></span> <span data-ttu-id="88f27-130">「 傳訊引擎不會自動對應已知 SOAP 標頭從要求訊息給回應訊息的值。</span><span class="sxs-lookup"><span data-stu-id="88f27-130">The Messaging Engine does not automatically map the values of known SOAP headers from the request message to the response message.</span></span> <span data-ttu-id="88f27-131">在建立 Web 服務的回應訊息時，您必須特別設定 SOAP 標頭值。</span><span class="sxs-lookup"><span data-stu-id="88f27-131">When creating the response message for a Web service, you must specifically set the SOAP header values.</span></span> <span data-ttu-id="88f27-132">下列命令是設定 SOAP 標頭內容屬性的最簡單的方法：</span><span class="sxs-lookup"><span data-stu-id="88f27-132">The following command is the simplest method of setting a SOAP header context property:</span></span>  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = "<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination xmlns=\"\">Home</Origination><Destination xmlns=\"\">Work</Destination> </OrigDest>"  
```  
  
 <span data-ttu-id="88f27-133">您也可以達到這藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="88f27-133">You can also achieve this by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88f27-134">如果**SOAP。UnknownHeaders**屬性為 null，BizTalk 會自動傳回未知的 SOAP 回應的 SOAP 要求中收到的標頭。</span><span class="sxs-lookup"><span data-stu-id="88f27-134">If the **SOAP.UnknownHeaders** property is null, BizTalk automatically returns the unknown headers received in the SOAP request to the SOAP response.</span></span> <span data-ttu-id="88f27-135">如果**SOAP。UnknownHeaders**回應訊息上的內容屬性不是 null，則 BizTalk 會將該值傳回至 SOAP 回應。</span><span class="sxs-lookup"><span data-stu-id="88f27-135">If the **SOAP.UnknownHeaders** context property on the response message is not null, then BizTalk returns that value to the SOAP response.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f27-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88f27-136">See Also</span></span>  
 [<span data-ttu-id="88f27-137">SOAP 標頭與已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="88f27-137">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)