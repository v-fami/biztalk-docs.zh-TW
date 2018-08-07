---
title: WCF 接收配接器 |Microsoft Docs
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
ms.openlocfilehash: 4c30d858c08da8a0f8d71d56397e43d591b3d773
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965831"
---
# <a name="wcf-receive-adapter"></a><span data-ttu-id="c98cb-102">WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="c98cb-102">WCF Receive Adapter</span></span>
<span data-ttu-id="c98cb-103">WCF 接收配接器可讓您接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="c98cb-103">The WCF receive adapter enables you to receive WCF service requests.</span></span>  
  
## <a name="extracting-the-biztalk-message-body-from-the-soap-message"></a><span data-ttu-id="c98cb-104">從 SOAP 訊息擷取 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="c98cb-104">Extracting the BizTalk Message Body from the SOAP Message</span></span>  
 <span data-ttu-id="c98cb-105">使用下列其中一種選項，便可從 SOAP 訊息擷取輸入 BizTalk 訊息內文：</span><span class="sxs-lookup"><span data-stu-id="c98cb-105">The inbound BizTalk message body can be extracted from the SOAP message by using one of the following options:</span></span>  
  
- <span data-ttu-id="c98cb-106">擷取 SOAP Body 元素的內容</span><span class="sxs-lookup"><span data-stu-id="c98cb-106">Extract the content of the SOAP Body element</span></span>  
  
- <span data-ttu-id="c98cb-107">擷取整個 SOAP Envelope</span><span class="sxs-lookup"><span data-stu-id="c98cb-107">Extract the entire SOAP envelope</span></span>  
  
- <span data-ttu-id="c98cb-108">使用 XPath 運算式以擷取 SOAP Envelope 內元素的內容</span><span class="sxs-lookup"><span data-stu-id="c98cb-108">Extract the content of the element inside the SOAP envelope by using an XPath expression</span></span>  
  
  <span data-ttu-id="c98cb-109">您可以在傳輸屬性對話方塊中設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="c98cb-109">You can configure these options in the transport properties dialog box.</span></span>  
  
#### <a name="extract-the-content-of-the-soap-body-element"></a><span data-ttu-id="c98cb-110">擷取 SOAP Body 元素的內容</span><span class="sxs-lookup"><span data-stu-id="c98cb-110">Extract the Content of the SOAP Body Element</span></span>  
 <span data-ttu-id="c98cb-111">若是選取這個選項，SOAP Body 元素的內部內容就會讀取自 SOAP 訊息，並且放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="c98cb-111">When this option is selected, the inner content of the SOAP Body element is read from the SOAP message and placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-entire-soap-envelope"></a><span data-ttu-id="c98cb-112">擷取整個 SOAP Envelope</span><span class="sxs-lookup"><span data-stu-id="c98cb-112">Extract the Entire SOAP Envelope</span></span>  
 <span data-ttu-id="c98cb-113">若是選取這個選項，包括標記的整個 SOAP Envelope 就會放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="c98cb-113">When this option is selected, the entire SOAP envelope including the tag is placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-content-of-the-element-by-using-an-xpath-expression"></a><span data-ttu-id="c98cb-114">使用 XPath 運算式以擷取元素的內容</span><span class="sxs-lookup"><span data-stu-id="c98cb-114">Extract the Content of the Element by Using an XPath Expression</span></span>  
 <span data-ttu-id="c98cb-115">若是選取這個選項，由 XPath 運算式所找出 SOAP Body 內元素的內部內容就會放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="c98cb-115">When this option is selected, the inner content of the element inside the SOAP Body element that is located by the XPath expression is placed into the body part of the BizTalk message.</span></span> <span data-ttu-id="c98cb-116">內文元素中的其他資料則會略過。</span><span class="sxs-lookup"><span data-stu-id="c98cb-116">The rest of the data in the Body element is ignored.</span></span> <span data-ttu-id="c98cb-117">您也必須指定節點編碼 -- 例如，XML、Base64、Hex 或 String 編碼。</span><span class="sxs-lookup"><span data-stu-id="c98cb-117">You also need to specify the node encoding—for example, XML, Base64, Hex, or String encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c98cb-118">若是選取 XML 編碼，XML 本文內元素的外部內容就會由 XPath 運算式所找出，並放入 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="c98cb-118">When the XML encoding is selected, the outer content of the element is located by the XPath expression and placed into the body part.</span></span>  
  
## <a name="handling-web-services-headers"></a><span data-ttu-id="c98cb-119">處理 Web 服務標頭</span><span class="sxs-lookup"><span data-stu-id="c98cb-119">Handling Web Services Headers</span></span>  
 <span data-ttu-id="c98cb-120">接收配接器會將標準 Web 服務標頭的子集升級到 BizTalk 訊息內容，以利根據這些標頭的值來輕鬆進行存取和路由。</span><span class="sxs-lookup"><span data-stu-id="c98cb-120">The receive adapter promotes a subset of the standard Web services headers onto the BizTalk message context to enable easy access and routing based on values of those headers.</span></span> <span data-ttu-id="c98cb-121">下表列出將由接收配接器儲存到訊息內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="c98cb-121">The following table lists the properties that will be saved onto the message context by the receive adapter.</span></span> <span data-ttu-id="c98cb-122">在下列命名空間下定義的屬性：http://www.w3.org/2005/addressing和http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties。</span><span class="sxs-lookup"><span data-stu-id="c98cb-122">The properties are defined under the following namespaces: http://www.w3.org/2005/addressing and http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.</span></span>  
  
|<span data-ttu-id="c98cb-123">標頭</span><span class="sxs-lookup"><span data-stu-id="c98cb-123">Header</span></span>|<span data-ttu-id="c98cb-124">BizTalk 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c98cb-124">BizTalk property name</span></span>|<span data-ttu-id="c98cb-125">是否有提升？</span><span class="sxs-lookup"><span data-stu-id="c98cb-125">Is promoted?</span></span>|  
|------------|---------------------------|------------------|  
|<span data-ttu-id="c98cb-126">動作</span><span class="sxs-lookup"><span data-stu-id="c98cb-126">Action</span></span>|<span data-ttu-id="c98cb-127">動作</span><span class="sxs-lookup"><span data-stu-id="c98cb-127">Action</span></span>|<span data-ttu-id="c98cb-128">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-128">Yes</span></span>|  
|<span data-ttu-id="c98cb-129">MessageID</span><span class="sxs-lookup"><span data-stu-id="c98cb-129">MessageID</span></span>|<span data-ttu-id="c98cb-130">MessageID</span><span class="sxs-lookup"><span data-stu-id="c98cb-130">MessageID</span></span>|<span data-ttu-id="c98cb-131">否</span><span class="sxs-lookup"><span data-stu-id="c98cb-131">No</span></span>|  
|<span data-ttu-id="c98cb-132">若要</span><span class="sxs-lookup"><span data-stu-id="c98cb-132">To</span></span>|<span data-ttu-id="c98cb-133">若要</span><span class="sxs-lookup"><span data-stu-id="c98cb-133">To</span></span>|<span data-ttu-id="c98cb-134">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-134">Yes</span></span>|  
|<span data-ttu-id="c98cb-135">ReplyTo/Address</span><span class="sxs-lookup"><span data-stu-id="c98cb-135">ReplyTo/Address</span></span>|<span data-ttu-id="c98cb-136">ReplyTo</span><span class="sxs-lookup"><span data-stu-id="c98cb-136">ReplyTo</span></span>|<span data-ttu-id="c98cb-137">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-137">Yes</span></span>|  
|<span data-ttu-id="c98cb-138">From/Address</span><span class="sxs-lookup"><span data-stu-id="c98cb-138">From/Address</span></span>|<span data-ttu-id="c98cb-139">來源</span><span class="sxs-lookup"><span data-stu-id="c98cb-139">From</span></span>|<span data-ttu-id="c98cb-140">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-140">Yes</span></span>|  
|<span data-ttu-id="c98cb-141">Sequence/Identifier</span><span class="sxs-lookup"><span data-stu-id="c98cb-141">Sequence/Identifier</span></span>|<span data-ttu-id="c98cb-142">SequenceId</span><span class="sxs-lookup"><span data-stu-id="c98cb-142">SequenceId</span></span>|<span data-ttu-id="c98cb-143">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-143">Yes</span></span>|  
|<span data-ttu-id="c98cb-144">Sequence/MessageNumber</span><span class="sxs-lookup"><span data-stu-id="c98cb-144">Sequence/MessageNumber</span></span>|<span data-ttu-id="c98cb-145">SequenceNumber</span><span class="sxs-lookup"><span data-stu-id="c98cb-145">SequenceNumber</span></span>|<span data-ttu-id="c98cb-146">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-146">Yes</span></span>|  
|<span data-ttu-id="c98cb-147">Sequence/LastMessage</span><span class="sxs-lookup"><span data-stu-id="c98cb-147">Sequence/LastMessage</span></span>|<span data-ttu-id="c98cb-148">SequenceLastMessage</span><span class="sxs-lookup"><span data-stu-id="c98cb-148">SequenceLastMessage</span></span>|<span data-ttu-id="c98cb-149">是</span><span class="sxs-lookup"><span data-stu-id="c98cb-149">Yes</span></span>|  
|<span data-ttu-id="c98cb-150">\<soap: Header\></span><span class="sxs-lookup"><span data-stu-id="c98cb-150">\<soap:Header\></span></span>|<span data-ttu-id="c98cb-151">InboundHeaders</span><span class="sxs-lookup"><span data-stu-id="c98cb-151">InboundHeaders</span></span>|<span data-ttu-id="c98cb-152">否</span><span class="sxs-lookup"><span data-stu-id="c98cb-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c98cb-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c98cb-153">See Also</span></span>  
 <span data-ttu-id="c98cb-154">[指定 WCF 配接器的訊息內文](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="c98cb-154">[Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span></span>  
 <span data-ttu-id="c98cb-155">[WCF 傳送配接器](../core/wcf-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c98cb-155">[WCF Send Adapter](../core/wcf-send-adapter.md) </span></span>  
 [<span data-ttu-id="c98cb-156">何謂 WCF 配接器？</span><span class="sxs-lookup"><span data-stu-id="c98cb-156">What Are the WCF Adapters?</span></span>](../core/what-are-the-wcf-adapters.md)