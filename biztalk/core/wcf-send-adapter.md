---
title: "WCF 傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- serializing, SOAP messages
- WCF adapters, extracting information
- messages, extracting information
- SOAP messages, serializing
- WCF adapters, message bodies
- send adapters, WCF adapters
- Web services, headers
- WCF adapters, send adapters
ms.assetid: 226a020a-2e12-41fe-a4a2-6683d9e98219
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70604fbc15f5f15b0a7ff2325debdc28ac3a97c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-send-adapter"></a><span data-ttu-id="73bc4-102">WCF 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="73bc4-102">WCF Send Adapter</span></span>
<span data-ttu-id="73bc4-103">WCF 傳送埠可以讓您透過無類型合約來呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="73bc4-103">The WCF send adapter enables you to call a WCF service through the typeless contract.</span></span>  
  
## <a name="specifying-the-wcf-message-body"></a><span data-ttu-id="73bc4-104">指定 WCF 訊息內文</span><span class="sxs-lookup"><span data-stu-id="73bc4-104">Specifying the WCF Message Body</span></span>  
 <span data-ttu-id="73bc4-105">需要從 BizTalk Server 傳送的訊息內文，可以使用下列一個選項插入到 SOAP 訊息：</span><span class="sxs-lookup"><span data-stu-id="73bc4-105">The message body that needs to be sent from BizTalk Server can be inserted into the SOAP message by using one of the following options:</span></span>  
  
-   <span data-ttu-id="73bc4-106">擷取 BizTalk 訊息內文的內容</span><span class="sxs-lookup"><span data-stu-id="73bc4-106">Extract the content of the BizTalk message body</span></span>  
  
-   <span data-ttu-id="73bc4-107">藉由使用範本來指定內容</span><span class="sxs-lookup"><span data-stu-id="73bc4-107">Specify the content by using the template</span></span>  
  
 <span data-ttu-id="73bc4-108">您可以在傳送埠傳輸屬性對話方塊中設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="73bc4-108">You can configure these options in the send port transport properties dialog box.</span></span>  
  
#### <a name="extract-the-content-of-the-biztalk-message-body"></a><span data-ttu-id="73bc4-109">擷取 BizTalk 訊息內文的內容</span><span class="sxs-lookup"><span data-stu-id="73bc4-109">Extract the Content of the BizTalk Message Body</span></span>  
 <span data-ttu-id="73bc4-110">選取這個選項時，會針對輸出 WCF 訊息內文，將 BizTalk 訊息內文的內容插入到 SOAP 內文項目。</span><span class="sxs-lookup"><span data-stu-id="73bc4-110">When this option is selected, the content of the BizTalk message body is inserted into the SOAP Body element for the outbound WCF message body.</span></span>  
  
#### <a name="specify-the-content-by-using-the-template"></a><span data-ttu-id="73bc4-111">藉由使用範本來指定內容</span><span class="sxs-lookup"><span data-stu-id="73bc4-111">Specify the Content by Using the Template</span></span>  
 <span data-ttu-id="73bc4-112">選取這個選項時，會針對輸出 WCF 訊息內文，將 BizTalk 訊息內文置放於 SOAP Body 項目中的指定 XML 範本下。</span><span class="sxs-lookup"><span data-stu-id="73bc4-112">When this option is selected, the BizTalk message body is placed in the SOAP body element under the given XML template for the outbound WCF message body.</span></span>  
  
## <a name="serializing-the-biztalk-message-into-a-soap-message"></a><span data-ttu-id="73bc4-113">將 BizTalk 訊息序列化到 SOAP 訊息中</span><span class="sxs-lookup"><span data-stu-id="73bc4-113">Serializing the BizTalk Message into a SOAP Message</span></span>  
 <span data-ttu-id="73bc4-114">傳送配接器在將 BizTalk 訊息傳送出去前，會先將訊息序列化於 SOAP 訊息中。訊息序列化期間會套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="73bc4-114">The send adapter serializes the BizTalk message into a SOAP message before sending it out. The following rules apply during serialization of the message:</span></span>  
  
-   <span data-ttu-id="73bc4-115">如果 BizTalk 訊息是多部分訊息，則只會使用內文部分。</span><span class="sxs-lookup"><span data-stu-id="73bc4-115">If the BizTalk message is a multipart message, then only the body part is used.</span></span>  
  
-   <span data-ttu-id="73bc4-116">如果 BizTalk 訊息包含整個 SOAP 信封，則會包裝到另一個 SOAP 信封中。</span><span class="sxs-lookup"><span data-stu-id="73bc4-116">If the BizTalk message contains the entire SOAP envelope, then it is wrapped into another SOAP envelope.</span></span>  
  
-   <span data-ttu-id="73bc4-117">如果 BizTalk 訊息包含任意 XML 資料，則會將 BizTalk 訊息置放於 SOAP Body 項目中。</span><span class="sxs-lookup"><span data-stu-id="73bc4-117">If the BizTalk message contains arbitrary XML data, then the BizTalk message is placed into the SOAP Body element.</span></span>  
  
## <a name="handling-web-services-headers"></a><span data-ttu-id="73bc4-118">處理 Web 服務標頭</span><span class="sxs-lookup"><span data-stu-id="73bc4-118">Handling Web Services Headers</span></span>  
 <span data-ttu-id="73bc4-119">傳送作業期間，BizTalk Server 無法控制 Web 服務的標準標頭。</span><span class="sxs-lookup"><span data-stu-id="73bc4-119">During send operations BizTalk Server does not have control over Web services standard headers.</span></span> <span data-ttu-id="73bc4-120">這些標頭是由 WCF 所設定和處理的。</span><span class="sxs-lookup"><span data-stu-id="73bc4-120">Those headers are set and processed by the WCF.</span></span> <span data-ttu-id="73bc4-121">可以修改 BizTalk Server 應用程式的唯一標準標頭**： 動作**標頭。</span><span class="sxs-lookup"><span data-stu-id="73bc4-121">The only standard header that can be modified by the BizTalk Server application is the **a:Action** header.</span></span> <span data-ttu-id="73bc4-122">如果內容屬性**動作**指定的配接器命名空間，則 WCF 傳送配接器會使用屬性的值來設定**動作**對 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="73bc4-122">If the context property **Action** is specified on the adapter namespace, then the WCF send adapter will use the value of the property to set the **Action** on the SOAP message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73bc4-123">動態傳送埠，如果**動作**中指定**OutboundHeaders**，為您設定的內容屬性**WCF。動作**會被忽略。</span><span class="sxs-lookup"><span data-stu-id="73bc4-123">For dynamic send ports, if **Action** is specified in the **OutboundHeaders**, the context property you set for the **WCF.Action** will be ignored.</span></span>  
  
## <a name="specifying-the-btsisdynamicsend-context-property"></a><span data-ttu-id="73bc4-124">指定 BTS.IsDynamicSend 內容屬性</span><span class="sxs-lookup"><span data-stu-id="73bc4-124">Specifying the BTS.IsDynamicSend Context Property</span></span>  
 <span data-ttu-id="73bc4-125">WCF 傳送配接器會快取傳送埠組態。</span><span class="sxs-lookup"><span data-stu-id="73bc4-125">The WCF send adapter caches the configuration for send ports.</span></span> <span data-ttu-id="73bc4-126">如果**BTS。IsDynamicSend**屬性設定為 true，則 WCF 傳送配接器不會使用快取的組態，但改為讀取所有組態資訊訊息輸出訊息的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="73bc4-126">If the **BTS.IsDynamicSend** property is set to true, the WCF send adapter does not use the cached configuration, but instead reads all configuration information from the message context properties of the outbound messages.</span></span> <span data-ttu-id="73bc4-127">在靜態傳送埠，WCF 傳送配接器會使用**BTS。SPLastUpdatedTime**、 上次修改靜態傳送埠設定的時間，來偵測是否有任何組態變更靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="73bc4-127">On a static send port, the WCF send adapter uses **BTS.SPLastUpdatedTime**, which is the time that the static send port settings were last modified, to detect if there are any configuration changes on the static send port.</span></span> <span data-ttu-id="73bc4-128">在這種方式下，WCF 傳送埠不需要從每個訊息內容讀取所有設定。</span><span class="sxs-lookup"><span data-stu-id="73bc4-128">In this way the WCF send adapter does not need to read all of the settings from every message context.</span></span>  
  
 <span data-ttu-id="73bc4-129">如果您想要覆寫靜態傳送埠屬性以外**WCF。動作**傳送管線中的屬性，您需要設定**BTS。IsDynamicSend**並未變更屬性設定為 true，因此即使上次更新時間戳記，WCF 傳送配接器不會使用快取的組態。</span><span class="sxs-lookup"><span data-stu-id="73bc4-129">If you want to override the static send port properties other than the **WCF.Action** property in a send pipeline, you need to set the **BTS.IsDynamicSend** property to true so that the WCF send adapter will not use the cached configuration even though the last updated timestamp has not changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bc4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73bc4-130">See Also</span></span>  
 <span data-ttu-id="73bc4-131">[指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="73bc4-131">[Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span></span>  
 <span data-ttu-id="73bc4-132">[WCF 接收配接器](../core/wcf-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="73bc4-132">[WCF Receive Adapter](../core/wcf-receive-adapter.md) </span></span>  
 <span data-ttu-id="73bc4-133">[WCF 配接器有哪些？](../core/what-are-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="73bc4-133">[What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md) </span></span>  
 [<span data-ttu-id="73bc4-134">如何使用訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="73bc4-134">How to Use Message Context Properties</span></span>](../core/how-to-use-message-context-properties.md)