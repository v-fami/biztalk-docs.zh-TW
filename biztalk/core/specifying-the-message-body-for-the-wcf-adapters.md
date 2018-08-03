---
title: 指定 WCF 配接器的訊息內文 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF adapters, SOAP messages
- messages, WCF adapters
- WCF adapters, message bodies
- SOAP messages, WCF adapters
ms.assetid: b20364b7-0365-4636-b4d6-bde9c69b8dcb
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32e62da213c4fceaf54773c2fe44584f43de9155
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972138"
---
# <a name="specifying-the-message-body-for-the-wcf-adapters"></a><span data-ttu-id="2678e-102">指定 WCF 配接器的訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-102">Specifying the Message Body for the WCF Adapters</span></span>
<span data-ttu-id="2678e-103">您可以使用**訊息**索引標籤中，指定如何將 BizTalk 訊息內文取自內送的 SOAP 訊息，則 WCF 配接器，而 BizTalk 訊息內文的方式放在為傳出 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-103">You can use the **Messages** tab in the WCF adapters to specify how the BizTalk message body is extracted from an incoming SOAP message, and how the BizTalk message body is placed in an outgoing SOAP message.</span></span>  

## <a name="specifying-how-the-biztalk-message-body-is-extracted-from-an-incoming-soap-message"></a><span data-ttu-id="2678e-104">指定如何從內送 SOAP 訊息擷取 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-104">Specifying How the BizTalk Message Body Is Extracted from an Incoming SOAP Message</span></span>  
 <span data-ttu-id="2678e-105">您可以控制如何從透過 WCF 配接器內送的 SOAP 訊息建立輸入 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-105">You can control how to create the inbound BizTalk message body from the SOAP messages incoming through the WCF adapters.</span></span> <span data-ttu-id="2678e-106">下圖顯示**訊息**索引標籤的 Wcf-netnamedpipe 接收配接器和傳送配接器做為範例。</span><span class="sxs-lookup"><span data-stu-id="2678e-106">The following figures show the **Messages** tabs of the WCF-NetNamedPipe receive adapter and send adapter as examples.</span></span>  

 <span data-ttu-id="2678e-107">![[訊息] 索引標籤，在 WCF 接收配接器](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")</span><span class="sxs-lookup"><span data-stu-id="2678e-107">![The Messages tab in the WCF receive adapters](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")</span></span>  

 <span data-ttu-id="2678e-108">![[訊息] 索引標籤，在 WCF 傳送配接器](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")</span><span class="sxs-lookup"><span data-stu-id="2678e-108">![The Messages tab in the WCF send adapters](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")</span></span>  

 <span data-ttu-id="2678e-109">若要指定如何建立 BizTalk 訊息內文，選取下列選項之一**輸入 BizTalk 訊息內文**在上圖中的區段：</span><span class="sxs-lookup"><span data-stu-id="2678e-109">To specify how to create the BizTalk message body, select one of the following options in the **Inbound BizTalk message body** section in the preceding figures:</span></span>  

- <span data-ttu-id="2678e-110">**信封--整個\<: Envelope>\>**。</span><span class="sxs-lookup"><span data-stu-id="2678e-110">**Envelope -- entire \<soap:Envelope\>**.</span></span> <span data-ttu-id="2678e-111">使用 SOAP**信封**內送訊息建立 BizTalk 訊息內文部分的項目。</span><span class="sxs-lookup"><span data-stu-id="2678e-111">Uses the SOAP **Envelope** element of an incoming message to create the BizTalk message body part.</span></span> <span data-ttu-id="2678e-112">整個內送訊息會變成 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-112">The entire incoming message becomes the BizTalk message body.</span></span> <span data-ttu-id="2678e-113">您可以使用這個選項，建立合併所有標頭的 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-113">Use this option to create the BizTalk message body incorporating all the headers.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="2678e-114">SOAP 標頭會放置在訊息內容中，但不會自動升級。</span><span class="sxs-lookup"><span data-stu-id="2678e-114">The SOAP headers are placed in the message context, but they are not promoted automatically.</span></span> <span data-ttu-id="2678e-115">在自訂管線元件中可進行升級。</span><span class="sxs-lookup"><span data-stu-id="2678e-115">Promotion can be done in a custom pipeline component.</span></span>  

- <span data-ttu-id="2678e-116">**內文--內容\<soap: Body&gt\>項目**。</span><span class="sxs-lookup"><span data-stu-id="2678e-116">**Body -- contents of \<soap:Body\> element**.</span></span> <span data-ttu-id="2678e-117">使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。</span><span class="sxs-lookup"><span data-stu-id="2678e-117">Uses the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part.</span></span> <span data-ttu-id="2678e-118">如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="2678e-118">If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.</span></span>  

- <span data-ttu-id="2678e-119">**路徑--內容由內文路徑放**。</span><span class="sxs-lookup"><span data-stu-id="2678e-119">**Path -- content located by body path**.</span></span> <span data-ttu-id="2678e-120">使用中的內文路徑運算式**內文路徑運算式**文字方塊中，建立 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="2678e-120">Uses the body path expression in the **Body path expression** text box to create the BizTalk message body part.</span></span> <span data-ttu-id="2678e-121">內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。</span><span class="sxs-lookup"><span data-stu-id="2678e-121">The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message.</span></span> <span data-ttu-id="2678e-122">當內送訊息有二進位資料時，您可以使用這個選項，讓 BizTalk 訊息內文部分只包含二進位資料，沒有任何標籤。</span><span class="sxs-lookup"><span data-stu-id="2678e-122">When incoming messages have binary data, you can use this option for the BizTalk message body to include only the binary data without any tags.</span></span>  

  <span data-ttu-id="2678e-123">當**路徑--內容由內文路徑定位**選取選項，則**節點編碼**屬性可以設定來指定預期的編碼類型的內文路徑運算式所指定的節點**內文路徑運算式**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2678e-123">When the **Path -- content located by body path** option is selected, the **Node encoding** property can be configured to specify the expected encoding type for the node specified by the body path expression in the **Body path expression** text box.</span></span> <span data-ttu-id="2678e-124">如果內文路徑運算式有一個以上相符的項目，只會使用第一個相符項目。</span><span class="sxs-lookup"><span data-stu-id="2678e-124">If the body path expression matches more than one element, only the first matched element is used.</span></span>  

> [!NOTE]
>  <span data-ttu-id="2678e-125">針對**內文路徑運算式**屬性，僅支援適用於順向處理 XML 的運算式的 XPath。</span><span class="sxs-lookup"><span data-stu-id="2678e-125">For the **body path expression** property, only the XPath expressions suitable for forward-only processing of XML are supported.</span></span> <span data-ttu-id="2678e-126">適用於此屬性的 XPath 運算式的詳細資訊，請參閱 「 最佳的兩個世界:: 結合 XPath 與 XmlReader 」，網址[ http://go.microsoft.com/fwlink/?LinkID=75701 ](http://go.microsoft.com/fwlink/?LinkID=75701)。</span><span class="sxs-lookup"><span data-stu-id="2678e-126">For more information about the XPath expressions available for this property, see "The Best of Both Worlds: Combining XPath with the XmlReader" at [http://go.microsoft.com/fwlink/?LinkID=75701](http://go.microsoft.com/fwlink/?LinkID=75701).</span></span>  

 <span data-ttu-id="2678e-127">如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**字串**，WCF 配接器預期相符的節點有 utf-8編碼字元資料。</span><span class="sxs-lookup"><span data-stu-id="2678e-127">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **String**, the WCF adapters expect that the matched node has UTF-8 encoded character data.</span></span> <span data-ttu-id="2678e-128">如果內送訊息包含逸出 XML 特殊字元的字元資料這類\<和\>，WCF 配接器建立 BizTalk 訊息內文部分時，請還原逸出的字元資料。</span><span class="sxs-lookup"><span data-stu-id="2678e-128">If the incoming messages include escaped character data for the XML special characters such as \< and \>, the WCF adapters restore the escaped character data when creating the BizTalk message body part.</span></span> <span data-ttu-id="2678e-129">例如，如果相符的節點有逸出字元資料這類**&lt;FirstName&gt;CONTOSO&lt;/FirstName&gt;** WCF 配接器建立**\<FirstName\>CONTOSO\</FirstName\>** 中輸入 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-129">For example, if the matched node has escaped character data such as **&lt;FirstName&gt;CONTOSO&lt;/FirstName&gt;** the WCF adapters create **\<FirstName\>CONTOSO\</FirstName\>** in the inbound BizTalk message body.</span></span>  

 <span data-ttu-id="2678e-130">如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**Hex**或**Base64**，相符的節點可以擁有有效**BinHex**或是**Base64**順序。</span><span class="sxs-lookup"><span data-stu-id="2678e-130">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **Hex** or **Base64**, the matched node can have a valid **BinHex** or **Base64** sequence.</span></span> <span data-ttu-id="2678e-131">如果相符的節點有無效序列，WCF 用戶端會收到**FaultException**、 BizTalk Server 電腦上，事件記錄檔會記錄一則錯誤訊息，並不會擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-131">If the matched node has an invalid sequence, the WCF client receives **FaultException**, an error message is logged in the event log on your BizTalk Server computer, and no message is suspended.</span></span>  

 <span data-ttu-id="2678e-132">如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**XML**，WCF 配接器建立 BizTalk 訊息內文與中的內文路徑運算式所選取之節點外部 XML**內文路徑運算式**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2678e-132">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **XML**, the WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the **Body path expression** text box.</span></span>  

 <span data-ttu-id="2678e-133">如果相符的節點沒有編碼形式的資料中的指定**節點編碼**屬性，建立空白的輸入的 BizTalk 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-133">If the matched node does not have data encoded as specified in the **Node encoding** property, an empty inbound BizTalk message body is created.</span></span>  

 <span data-ttu-id="2678e-134">例如，假設 WCF 傳送配接器從 WCF 用戶端接收下列 SOAP 訊息：</span><span class="sxs-lookup"><span data-stu-id="2678e-134">For example, suppose the WCF send adapters receive the following SOAP message from WCF clients:</span></span>  

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/OrderRefresh</a:Action>   
    <a:MessageID>urn:uuid:59e74507-66d0-4d50-be70-c3ec248b6f78</a:MessageID>   
    <a:ReplyTo>  
       <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>   
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>   
  </s:Header>  
  <s:Body>  
    <Order xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
     <OrderDetail>  
       <CustomerID>CONTOSO</CustomerID>   
       <OrderID>00000000</OrderID>   
     </OrderDetail>  
    </Order>  
  </s:Body>  
</s:Envelope>  
```  

 <span data-ttu-id="2678e-135">如果您設定**輸入 BizTalk 訊息內文**下表中，先前的內送 SOAP 訊息中所示的區段會變成輸入的 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="2678e-135">If you configure the **Inbound BizTalk message body** section as shown in the following table, the previous incoming SOAP message becomes the inbound BizTalk message body part.</span></span>  

|<span data-ttu-id="2678e-136">輸入 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-136">Inbound BizTalk message body</span></span>|<span data-ttu-id="2678e-137">[內文路徑運算式]</span><span class="sxs-lookup"><span data-stu-id="2678e-137">Body path expression</span></span>|<span data-ttu-id="2678e-138">節點編碼</span><span class="sxs-lookup"><span data-stu-id="2678e-138">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="2678e-139">**信封--整個\<: Envelope>\>**</span><span class="sxs-lookup"><span data-stu-id="2678e-139">**Envelope -- entire \<soap:Envelope\>**</span></span>|<span data-ttu-id="2678e-140">不適用</span><span class="sxs-lookup"><span data-stu-id="2678e-140">N/A</span></span>|<span data-ttu-id="2678e-141">不適用</span><span class="sxs-lookup"><span data-stu-id="2678e-141">N/A</span></span>|  

 <span data-ttu-id="2678e-142">如果您設定**BizTalk 訊息內文**一節下表所示，WCF 配接器會建立輸入的 BizTalk 訊息內文部分使其只包含**順序**在上一個項目內送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-142">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters create the inbound BizTalk message body part to contain only the **Order** element in the previous incoming SOAP message.</span></span>  

|<span data-ttu-id="2678e-143">輸入 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-143">Inbound BizTalk message body</span></span>|<span data-ttu-id="2678e-144">[內文路徑運算式]</span><span class="sxs-lookup"><span data-stu-id="2678e-144">Body path expression</span></span>|<span data-ttu-id="2678e-145">節點編碼</span><span class="sxs-lookup"><span data-stu-id="2678e-145">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="2678e-146">**內文--內容\<soap: Body&gt\>項目**</span><span class="sxs-lookup"><span data-stu-id="2678e-146">**Body -- contents of \<soap:Body\> element**</span></span>|<span data-ttu-id="2678e-147">不適用</span><span class="sxs-lookup"><span data-stu-id="2678e-147">N/A</span></span>|<span data-ttu-id="2678e-148">不適用</span><span class="sxs-lookup"><span data-stu-id="2678e-148">N/A</span></span>|  

 <span data-ttu-id="2678e-149">如果您設定**BizTalk 訊息內文** 區段下表所示，WCF 配接器會預期內文路徑運算式相符的連入節點將有 utf-8 編碼字元資料。</span><span class="sxs-lookup"><span data-stu-id="2678e-149">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters expect that the incoming node that the body path expression matches will have UTF-8 encoded character data.</span></span>  

|<span data-ttu-id="2678e-150">輸入 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-150">Inbound BizTalk message body</span></span>|<span data-ttu-id="2678e-151">[內文路徑運算式]</span><span class="sxs-lookup"><span data-stu-id="2678e-151">Body path expression</span></span>|<span data-ttu-id="2678e-152">節點編碼</span><span class="sxs-lookup"><span data-stu-id="2678e-152">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="2678e-153">**路徑--內容由內文路徑定位**</span><span class="sxs-lookup"><span data-stu-id="2678e-153">**Path -- content located by body path**</span></span>|<span data-ttu-id="2678e-154">/ \* [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']</span><span class="sxs-lookup"><span data-stu-id="2678e-154">/\*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="2678e-155">**String**</span><span class="sxs-lookup"><span data-stu-id="2678e-155">**String**</span></span>|  

 <span data-ttu-id="2678e-156">如上面的內送 SOAP 訊息，WCF 配接器使用的字元資料**CONTOSO**的**CustomerID**元素，來建立輸入的 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="2678e-156">For the previous incoming SOAP message, the WCF adapters use the character data, **CONTOSO**, of the **CustomerID** element to create the inbound BizTalk message body part.</span></span>  

> [!NOTE]
>  <span data-ttu-id="2678e-157">您無法使用 XPath 縮寫的語法 **/Order/OrderDetail/CustomerID**，如上面的內送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-157">You cannot use the abbreviated syntax of XPath, **/Order/OrderDetail/CustomerID**, for the previous incoming SOAP message.</span></span> <span data-ttu-id="2678e-158">這是因為 XPath 縮寫的語法會傳回未宣告的命名空間中的節點並**CustomerID**上面的 SOAP 訊息中的項目中宣告**http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess**命名空間預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="2678e-158">This is because the abbreviated syntax of XPath returns the node not declared in a namespace, and the **CustomerID** element in the previous SOAP message is declared in the **http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess** namespace by default namespaces.</span></span>  

 <span data-ttu-id="2678e-159">如果您設定**BizTalk 訊息內文**區段下表所示**CustomID**上面的內送 SOAP 訊息中的項目應具有有效**BinHex**或是**Base64**順序。</span><span class="sxs-lookup"><span data-stu-id="2678e-159">If you configure the **BizTalk message body** section as shown in the following table, the **CustomID** element in the previous incoming SOAP message should have a valid **BinHex** or **Base64** sequence.</span></span>  

|<span data-ttu-id="2678e-160">輸入 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-160">Inbound BizTalk message body</span></span>|<span data-ttu-id="2678e-161">[內文路徑運算式]</span><span class="sxs-lookup"><span data-stu-id="2678e-161">Body path expression</span></span>|<span data-ttu-id="2678e-162">節點編碼</span><span class="sxs-lookup"><span data-stu-id="2678e-162">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="2678e-163">**路徑--內容由內文路徑定位**</span><span class="sxs-lookup"><span data-stu-id="2678e-163">**Path -- content located by body path**</span></span>|<span data-ttu-id="2678e-164">/ \* [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']</span><span class="sxs-lookup"><span data-stu-id="2678e-164">/\*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="2678e-165">**Hex**或**Base64**</span><span class="sxs-lookup"><span data-stu-id="2678e-165">**Hex** or **Base64**</span></span>|  

 <span data-ttu-id="2678e-166">如果您設定**BizTalk 訊息內文** 區段下表所示，WCF 配接器建立輸入的 BizTalk 訊息內文，如上面的內送 SOAP 訊息中所示的程式碼表格之後。</span><span class="sxs-lookup"><span data-stu-id="2678e-166">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters create the inbound BizTalk message body for the previous incoming SOAP message as shown in the code after the table.</span></span>  

|<span data-ttu-id="2678e-167">輸入 BizTalk 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-167">Inbound BizTalk message body</span></span>|<span data-ttu-id="2678e-168">[內文路徑運算式]</span><span class="sxs-lookup"><span data-stu-id="2678e-168">Body path expression</span></span>|<span data-ttu-id="2678e-169">節點編碼</span><span class="sxs-lookup"><span data-stu-id="2678e-169">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="2678e-170">**路徑--內容由內文路徑定位**</span><span class="sxs-lookup"><span data-stu-id="2678e-170">**Path -- content located by body path**</span></span>|<span data-ttu-id="2678e-171">/ \* [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']</span><span class="sxs-lookup"><span data-stu-id="2678e-171">/\*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="2678e-172">**XML**</span><span class="sxs-lookup"><span data-stu-id="2678e-172">**XML**</span></span>|  

```  
<CustomerID xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">CONTOSO</CustomerID>   
```  

## <a name="specifying-the-source-of-the-outbound-wcf-message-body"></a><span data-ttu-id="2678e-173">指定輸出 WCF 訊息內文的來源</span><span class="sxs-lookup"><span data-stu-id="2678e-173">Specifying the Source of the Outbound WCF Message Body</span></span>  
 <span data-ttu-id="2678e-174">您可以控制如何從 BizTalk 訊息內文建立輸出 WCF 訊息內文，以透過 WCF 配接器傳送。</span><span class="sxs-lookup"><span data-stu-id="2678e-174">You can control how to create the outbound WCF message body from a BizTalk message body to send through the WCF adapters.</span></span> <span data-ttu-id="2678e-175">若要指定 BizTalk 訊息內文放置在 輸出 WCF 訊息內文的方式，您可以使用下列選項之一**輸出 WCF 訊息內文**區段**訊息**索引標籤中所示上一節中的數字：</span><span class="sxs-lookup"><span data-stu-id="2678e-175">To specify how the BizTalk message body is placed in the outbound WCF message body, you can use one of the following options in the **Outbound WCF message body** section on the **Messages** tab as shown in the figures in the previous section:</span></span>  

- <span data-ttu-id="2678e-176">**內文--BizTalk 回應訊息內文**。</span><span class="sxs-lookup"><span data-stu-id="2678e-176">**Body -- BizTalk response message body**.</span></span> <span data-ttu-id="2678e-177">使用 BizTalk 訊息內文部分建立的內容的 soap**主體**外寄訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="2678e-177">Uses the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.</span></span> <span data-ttu-id="2678e-178">外寄 BizTalk 訊息內文會變成輸出 SOAP 訊息的內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-178">The outgoing BizTalk message body becomes the body of the outbound SOAP message.</span></span>  

- <span data-ttu-id="2678e-179">**範本--內容由範本指定**。</span><span class="sxs-lookup"><span data-stu-id="2678e-179">**Template -- content specified by template**.</span></span> <span data-ttu-id="2678e-180">使用中提供的範本**XML**文字方塊中，若要建立內容的 SOAP**主體**外寄訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="2678e-180">Uses the template supplied in the **XML** text box to create the content of the SOAP **Body** element for an outgoing message.</span></span> <span data-ttu-id="2678e-181">使用 WCF 配接器**內文--BizTalk 回應訊息內文**（預設值） 選項不允許傳送非 XML 訊息，例如字元資料和點陣圖影像。</span><span class="sxs-lookup"><span data-stu-id="2678e-181">The WCF adapters with **Body -- BizTalk response message body** (the default value) option do not allow sending non-XML message such as character data and bitmap images.</span></span> <span data-ttu-id="2678e-182">您可以使用**範本--由範本指定的內容**選項，WCF 配接器傳送非 XML 訊息編碼**base64**，**十六進位**，或**字串**.</span><span class="sxs-lookup"><span data-stu-id="2678e-182">You can use the **Template -- content specified by template** option for the WCF adapters to send non-XML messages encoded in **base64**, **hex**, or **string**.</span></span>  

  <span data-ttu-id="2678e-183">當**範本--由範本指定的內容**選項，您必須提供任意範本 XML 項目中的**輸出 WCF 訊息內文-XML**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2678e-183">When the **Template -- content specified by template** option is selected, you must provide an arbitrary template XML element in the **Outbound WCF message body - XML** text box.</span></span> <span data-ttu-id="2678e-184">範本 XML 項目必須包含下列**bts 訊息主體**唯一的一次的項目除非範本 XML 項目保留為空白：</span><span class="sxs-lookup"><span data-stu-id="2678e-184">The template XML element must contain the following **bts-msg-body** element once and only once unless the template XML element is left empty:</span></span>  

```  
<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2010" encoding="[base64|hex|string|xml]"/>  
```  

 <span data-ttu-id="2678e-185">WCF 配接器編碼 BizTalk 訊息內文，根據**編碼**屬性中的 XML 範本，並取代**bts 訊息主體**編碼 BizTalk 訊息內文建立時的項目輸出 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-185">The WCF adapters encode the BizTalk message body according to the **encoding** attribute in the XML template, and then replace the **bts-msg-body** element with the encoded BizTalk message body when creating outbound WCF messages.</span></span> <span data-ttu-id="2678e-186">如果**輸出 WCF 訊息內文-XML**文字方塊留為空白，則 WCF 配接器編碼 BizTalk 訊息內文中的**Base64**，然後將放置**Base64**中序列輸出的 SOAP 訊息內文。</span><span class="sxs-lookup"><span data-stu-id="2678e-186">If the **Outbound WCF message body - XML** text box is left empty, the WCF adapters encode the BizTalk message body in **Base64**, and then place the **Base64** sequence in the outbound SOAP message body.</span></span>  

 <span data-ttu-id="2678e-187">如果**編碼**XML 範本中的屬性設定為**字串**，WCF 配接器會將 BizTalk 訊息內文部分編碼為 utf-8 編碼字元資料，在其中 XML 特殊字元，如\<和\>會逸出。</span><span class="sxs-lookup"><span data-stu-id="2678e-187">If the **encoding** attribute in the XML template is set to **string**, the WCF adapters encode the BizTalk message body part as UTF-8 encoded character data, in which the XML special characters such as \< and \> are escaped.</span></span>  

 <span data-ttu-id="2678e-188">如果**編碼**XML 範本中的屬性設定為**base64**或是**十六進位**，WCF 配接器編碼 BizTalk 訊息內文部分，做為**BinHex**或是**Base64**順序。</span><span class="sxs-lookup"><span data-stu-id="2678e-188">If the **encoding** attribute in the XML template is set to **base64** or **hex**, the WCF adapters encode the BizTalk message body part as a **BinHex** or **Base64** sequence.</span></span>  

 <span data-ttu-id="2678e-189">如果**編碼**XML 範本中的屬性設定為**xml**，則 WCF 配接器取代**bts 訊息主體**輸出 BizTalk 訊息內文，若要建立的項目外寄 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-189">If the **encoding** attribute in the XML template is set to **xml**, the WCF adapters replace the **bts-msg-body** element with the outbound BizTalk message body to create the outgoing WCF message.</span></span>  

 <span data-ttu-id="2678e-190">例如，假設 WCF 配接器必須將下列 BizTalk 訊息內文部分傳送至 WCF 用戶端：</span><span class="sxs-lookup"><span data-stu-id="2678e-190">For example, suppose the WCF adapters need to send the following BizTalk message body part to WCF clients:</span></span>  

```  
<ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
```  

 <span data-ttu-id="2678e-191">如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-191">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  

|<span data-ttu-id="2678e-192">輸出 WCF 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-192">Outbound WCF message body</span></span>|<span data-ttu-id="2678e-193">XML</span><span class="sxs-lookup"><span data-stu-id="2678e-193">XML</span></span>|  
|-------------------------------|---------|  
|<span data-ttu-id="2678e-194">**內文--BizTalk 回應訊息內文**</span><span class="sxs-lookup"><span data-stu-id="2678e-194">**Body -- BizTalk response message body**</span></span>|<span data-ttu-id="2678e-195">不適用</span><span class="sxs-lookup"><span data-stu-id="2678e-195">N/A</span></span>|  

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:6a706a54-c4f5-4767-909d-a992c7c26dba</a:MessageID>  
    <a:ReplyTo>  
<a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
  </s:Body>  
</s:Envelope>  
```  

 <span data-ttu-id="2678e-196">如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-196">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  


|         <span data-ttu-id="2678e-197">輸出 WCF 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-197">Outbound WCF message body</span></span>         |                                                                    <span data-ttu-id="2678e-198">XML</span><span class="sxs-lookup"><span data-stu-id="2678e-198">XML</span></span>                                                                    |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2678e-199">**內文--BizTalk 回應訊息內文**</span><span class="sxs-lookup"><span data-stu-id="2678e-199">**Body -- BizTalk response message body**</span></span> | <span data-ttu-id="2678e-200">\<活頁簿\></span><span class="sxs-lookup"><span data-stu-id="2678e-200">\<Book\></span></span><br /><br /> <span data-ttu-id="2678e-201">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**string**"/\></span><span class="sxs-lookup"><span data-stu-id="2678e-201">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**string**"/\></span></span><br /><br /> <span data-ttu-id="2678e-202">\</Book\></span><span class="sxs-lookup"><span data-stu-id="2678e-202">\</Book\></span></span> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:05dde292-eedd-467e-b0d2-f1b8f0757410</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <Book><ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  <ns0:OrderDetail>    <ns0:CustomerID>CONTOSO</ns0:CustomerID>    <ns0:OrderID> 01A2c</ns0:OrderID>  </ns0:OrderDetail></ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```  

 <span data-ttu-id="2678e-203">如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-203">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  


|         <span data-ttu-id="2678e-204">輸出 WCF 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-204">Outbound WCF message body</span></span>         |                                                                    <span data-ttu-id="2678e-205">XML</span><span class="sxs-lookup"><span data-stu-id="2678e-205">XML</span></span>                                                                    |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2678e-206">**內文--BizTalk 回應訊息內文**</span><span class="sxs-lookup"><span data-stu-id="2678e-206">**Body -- BizTalk response message body**</span></span> | <span data-ttu-id="2678e-207">\<活頁簿\></span><span class="sxs-lookup"><span data-stu-id="2678e-207">\<Book\></span></span><br /><br /> <span data-ttu-id="2678e-208">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**base64**"/\></span><span class="sxs-lookup"><span data-stu-id="2678e-208">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**base64**"/\></span></span><br /><br /> <span data-ttu-id="2678e-209">\</Book\></span><span class="sxs-lookup"><span data-stu-id="2678e-209">\</Book\></span></span> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://ww  
w.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe  
/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:cb3cac6d-a542-4a90-bad8-cdbfa8251112</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessSer  
vice</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>77u/PG5zMDpPcmRlciB4bWxuczpuczA9Imh0dHA6Ly9NaWNyb3NvZnQuU2FtcGxlcy5CaX  
pUYWxrLk5ldE5hbWVkUGlwZS9PcmRlclByb2Nlc3MiPg0KICA8bnMwOk9yZGVyRGV0YWlsPg0KICAgID  
xuczA6Q3VzdG9tZXJJRD5DT05UT1NPPC9uczA6Q3VzdG9tZXJJRD4NCiAgICA8bnMwOk9yZGVySUQ+MD  
FBMmM8L25zMDpPcmRlcklEPg0KICA8L25zMDpPcmRlckRldGFpbD4NCjwvbnMwOk9yZGVyPg==</Book  
>  
  </s:Body>  
</s:Envelope>  
```  

 <span data-ttu-id="2678e-210">如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="2678e-210">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  


|         <span data-ttu-id="2678e-211">輸出 WCF 訊息內文</span><span class="sxs-lookup"><span data-stu-id="2678e-211">Outbound WCF message body</span></span>         |                                                                  <span data-ttu-id="2678e-212">XML</span><span class="sxs-lookup"><span data-stu-id="2678e-212">XML</span></span>                                                                   |
|-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2678e-213">**內文--BizTalk 回應訊息內文**</span><span class="sxs-lookup"><span data-stu-id="2678e-213">**Body -- BizTalk response message body**</span></span> | <span data-ttu-id="2678e-214">\<活頁簿\></span><span class="sxs-lookup"><span data-stu-id="2678e-214">\<Book\></span></span><br /><br /> <span data-ttu-id="2678e-215">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**xml**"/\></span><span class="sxs-lookup"><span data-stu-id="2678e-215">\<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**xml**"/\></span></span><br /><br /> <span data-ttu-id="2678e-216">\</Book\></span><span class="sxs-lookup"><span data-stu-id="2678e-216">\</Book\></span></span> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:A  
ction>  
    <a:MessageID>{513C123C-0600-4A1C-BEE2-EF83E0EFEB15}</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>  
      <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CustomerID_0</ns0:CustomerID>  
    <ns0:OrderID>OrderID_0</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```