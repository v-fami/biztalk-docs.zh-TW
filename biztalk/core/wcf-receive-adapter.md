---
title: WCF 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, headers
- receive adapters, Web service headers
- SOAP messages, extracting information
- SOAP messages, WCF adapters
- WCF adapters, receive adapters
- messages, SOAP
- receive adapters, WCF adapters
- Web services, headers
- headers [messages]
- SOAP messages, receive adapters
ms.assetid: 6b3d5df1-5d9d-4240-a98f-ea29c3272e38
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdd4d6335723d068333403b4c9d811d96db058e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972692"
---
# <a name="wcf-receive-adapter"></a><span data-ttu-id="ddf62-102">WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="ddf62-102">WCF Receive Adapter</span></span>
<span data-ttu-id="ddf62-103">WCF 接收配接器可讓您接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="ddf62-103">The WCF receive adapter enables you to receive WCF service requests.</span></span>  
  
## <a name="extracting-the-biztalk-message-body-from-the-soap-message"></a><span data-ttu-id="ddf62-104">從 SOAP 訊息擷取 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="ddf62-104">Extracting the BizTalk Message Body from the SOAP Message</span></span>  
 <span data-ttu-id="ddf62-105">使用下列其中一種選項，便可從 SOAP 訊息擷取輸入 BizTalk 訊息內文：</span><span class="sxs-lookup"><span data-stu-id="ddf62-105">The inbound BizTalk message body can be extracted from the SOAP message by using one of the following options:</span></span>  
  
-   <span data-ttu-id="ddf62-106">擷取 SOAP Body 元素的內容</span><span class="sxs-lookup"><span data-stu-id="ddf62-106">Extract the content of the SOAP Body element</span></span>  
  
-   <span data-ttu-id="ddf62-107">擷取整個 SOAP Envelope</span><span class="sxs-lookup"><span data-stu-id="ddf62-107">Extract the entire SOAP envelope</span></span>  
  
-   <span data-ttu-id="ddf62-108">使用 XPath 運算式以擷取 SOAP Envelope 內元素的內容</span><span class="sxs-lookup"><span data-stu-id="ddf62-108">Extract the content of the element inside the SOAP envelope by using an XPath expression</span></span>  
  
 <span data-ttu-id="ddf62-109">您可以在傳輸屬性對話方塊中設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="ddf62-109">You can configure these options in the transport properties dialog box.</span></span>  
  
#### <a name="extract-the-content-of-the-soap-body-element"></a><span data-ttu-id="ddf62-110">擷取 SOAP Body 元素的內容</span><span class="sxs-lookup"><span data-stu-id="ddf62-110">Extract the Content of the SOAP Body Element</span></span>  
 <span data-ttu-id="ddf62-111">若是選取這個選項，SOAP Body 元素的內部內容就會讀取自 SOAP 訊息，並且放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="ddf62-111">When this option is selected, the inner content of the SOAP Body element is read from the SOAP message and placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-entire-soap-envelope"></a><span data-ttu-id="ddf62-112">擷取整個 SOAP Envelope</span><span class="sxs-lookup"><span data-stu-id="ddf62-112">Extract the Entire SOAP Envelope</span></span>  
 <span data-ttu-id="ddf62-113">若是選取這個選項，包括標記的整個 SOAP Envelope 就會放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="ddf62-113">When this option is selected, the entire SOAP envelope including the tag is placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-content-of-the-element-by-using-an-xpath-expression"></a><span data-ttu-id="ddf62-114">使用 XPath 運算式以擷取元素的內容</span><span class="sxs-lookup"><span data-stu-id="ddf62-114">Extract the Content of the Element by Using an XPath Expression</span></span>  
 <span data-ttu-id="ddf62-115">若是選取這個選項，由 XPath 運算式所找出 SOAP Body 內元素的內部內容就會放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="ddf62-115">When this option is selected, the inner content of the element inside the SOAP Body element that is located by the XPath expression is placed into the body part of the BizTalk message.</span></span> <span data-ttu-id="ddf62-116">內文元素中的其他資料則會略過。</span><span class="sxs-lookup"><span data-stu-id="ddf62-116">The rest of the data in the Body element is ignored.</span></span> <span data-ttu-id="ddf62-117">您也必須指定節點編碼 -- 例如，XML、Base64、Hex 或 String 編碼。</span><span class="sxs-lookup"><span data-stu-id="ddf62-117">You also need to specify the node encoding—for example, XML, Base64, Hex, or String encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddf62-118">若是選取 XML 編碼，XML 本文內元素的外部內容就會由 XPath 運算式所找出，並放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="ddf62-118">When the XML encoding is selected, the outer content of the element is located by the XPath expression and placed into the body part.</span></span>  
  
## <a name="handling-web-services-headers"></a><span data-ttu-id="ddf62-119">處理 Web 服務標頭</span><span class="sxs-lookup"><span data-stu-id="ddf62-119">Handling Web Services Headers</span></span>  
 <span data-ttu-id="ddf62-120">接收配接器會將標準 Web 服務標頭的子集升級到 BizTalk 訊息內容，以利根據這些標頭的值來輕鬆進行存取和路由。</span><span class="sxs-lookup"><span data-stu-id="ddf62-120">The receive adapter promotes a subset of the standard Web services headers onto the BizTalk message context to enable easy access and routing based on values of those headers.</span></span> <span data-ttu-id="ddf62-121">下表列出將由接收配接器儲存到訊息內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="ddf62-121">The following table lists the properties that will be saved onto the message context by the receive adapter.</span></span> <span data-ttu-id="ddf62-122">在下列命名空間下定義的屬性： http://www.w3.org/2005/addressing 及 http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties。</span><span class="sxs-lookup"><span data-stu-id="ddf62-122">The properties are defined under the following namespaces: http://www.w3.org/2005/addressing and http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.</span></span>  
  
|<span data-ttu-id="ddf62-123">標頭</span><span class="sxs-lookup"><span data-stu-id="ddf62-123">Header</span></span>|<span data-ttu-id="ddf62-124">BizTalk 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="ddf62-124">BizTalk property name</span></span>|<span data-ttu-id="ddf62-125">是否有提升？</span><span class="sxs-lookup"><span data-stu-id="ddf62-125">Is promoted?</span></span>|  
|------------|---------------------------|------------------|  
|<span data-ttu-id="ddf62-126">動作</span><span class="sxs-lookup"><span data-stu-id="ddf62-126">Action</span></span>|<span data-ttu-id="ddf62-127">動作</span><span class="sxs-lookup"><span data-stu-id="ddf62-127">Action</span></span>|<span data-ttu-id="ddf62-128">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-128">Yes</span></span>|  
|<span data-ttu-id="ddf62-129">MessageID</span><span class="sxs-lookup"><span data-stu-id="ddf62-129">MessageID</span></span>|<span data-ttu-id="ddf62-130">MessageID</span><span class="sxs-lookup"><span data-stu-id="ddf62-130">MessageID</span></span>|<span data-ttu-id="ddf62-131">否</span><span class="sxs-lookup"><span data-stu-id="ddf62-131">No</span></span>|  
|<span data-ttu-id="ddf62-132">若要</span><span class="sxs-lookup"><span data-stu-id="ddf62-132">To</span></span>|<span data-ttu-id="ddf62-133">若要</span><span class="sxs-lookup"><span data-stu-id="ddf62-133">To</span></span>|<span data-ttu-id="ddf62-134">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-134">Yes</span></span>|  
|<span data-ttu-id="ddf62-135">ReplyTo/Address</span><span class="sxs-lookup"><span data-stu-id="ddf62-135">ReplyTo/Address</span></span>|<span data-ttu-id="ddf62-136">ReplyTo</span><span class="sxs-lookup"><span data-stu-id="ddf62-136">ReplyTo</span></span>|<span data-ttu-id="ddf62-137">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-137">Yes</span></span>|  
|<span data-ttu-id="ddf62-138">From/Address</span><span class="sxs-lookup"><span data-stu-id="ddf62-138">From/Address</span></span>|<span data-ttu-id="ddf62-139">來源</span><span class="sxs-lookup"><span data-stu-id="ddf62-139">From</span></span>|<span data-ttu-id="ddf62-140">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-140">Yes</span></span>|  
|<span data-ttu-id="ddf62-141">Sequence/Identifier</span><span class="sxs-lookup"><span data-stu-id="ddf62-141">Sequence/Identifier</span></span>|<span data-ttu-id="ddf62-142">SequenceId</span><span class="sxs-lookup"><span data-stu-id="ddf62-142">SequenceId</span></span>|<span data-ttu-id="ddf62-143">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-143">Yes</span></span>|  
|<span data-ttu-id="ddf62-144">Sequence/MessageNumber</span><span class="sxs-lookup"><span data-stu-id="ddf62-144">Sequence/MessageNumber</span></span>|<span data-ttu-id="ddf62-145">SequenceNumber</span><span class="sxs-lookup"><span data-stu-id="ddf62-145">SequenceNumber</span></span>|<span data-ttu-id="ddf62-146">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-146">Yes</span></span>|  
|<span data-ttu-id="ddf62-147">Sequence/LastMessage</span><span class="sxs-lookup"><span data-stu-id="ddf62-147">Sequence/LastMessage</span></span>|<span data-ttu-id="ddf62-148">SequenceLastMessage</span><span class="sxs-lookup"><span data-stu-id="ddf62-148">SequenceLastMessage</span></span>|<span data-ttu-id="ddf62-149">是</span><span class="sxs-lookup"><span data-stu-id="ddf62-149">Yes</span></span>|  
|<span data-ttu-id="ddf62-150">\<soap： 標頭\></span><span class="sxs-lookup"><span data-stu-id="ddf62-150">\<soap:Header\></span></span>|<span data-ttu-id="ddf62-151">InboundHeaders</span><span class="sxs-lookup"><span data-stu-id="ddf62-151">InboundHeaders</span></span>|<span data-ttu-id="ddf62-152">否</span><span class="sxs-lookup"><span data-stu-id="ddf62-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddf62-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddf62-153">See Also</span></span>  
 <span data-ttu-id="ddf62-154">[指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="ddf62-154">[Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span></span>  
 <span data-ttu-id="ddf62-155">[WCF 傳送配接器](../core/wcf-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ddf62-155">[WCF Send Adapter](../core/wcf-send-adapter.md) </span></span>  
 [<span data-ttu-id="ddf62-156">何謂 WCF 配接器？</span><span class="sxs-lookup"><span data-stu-id="ddf62-156">What Are the WCF Adapters?</span></span>](../core/what-are-the-wcf-adapters.md)