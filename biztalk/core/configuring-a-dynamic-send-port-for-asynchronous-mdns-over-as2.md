---
title: 設定透過 AS2 之非同步 Mdn 的動態傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72646c90-89db-4884-824b-6921bb824f8d
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 754917ed1a089e3182c8543e8a132a9eff73615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233446"
---
# <a name="configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2"></a><span data-ttu-id="d3483-102">設定透過 AS2 之非同步 MDN 的動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="d3483-102">Configuring a Dynamic Send Port for Asynchronous MDNs over AS2</span></span>
<span data-ttu-id="d3483-103">若要透過 HTTP/HTTPS 傳送非同步的 EDIINT/AS2 編碼 MDN 訊息，請建立包含下列組態的動態 HTTP 傳送埠：</span><span class="sxs-lookup"><span data-stu-id="d3483-103">To send an asynchronous EDIINT/AS2-encoded MDN message over HTTP/HTTPS, create a dynamic HTTP send port with the following configuration:</span></span>  
  
|<span data-ttu-id="d3483-104">位置</span><span class="sxs-lookup"><span data-stu-id="d3483-104">Location</span></span>|<span data-ttu-id="d3483-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d3483-105">Property</span></span>|<span data-ttu-id="d3483-106">設定</span><span class="sxs-lookup"><span data-stu-id="d3483-106">Setting</span></span>|  
|--------------|--------------|-------------|  
|<span data-ttu-id="d3483-107">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="d3483-107">**Send Port Properties: General**</span></span>|<span data-ttu-id="d3483-108">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="d3483-108">Port Type</span></span>|<span data-ttu-id="d3483-109">動態單向</span><span class="sxs-lookup"><span data-stu-id="d3483-109">Dynamic One-Way</span></span>|  
|<span data-ttu-id="d3483-110">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="d3483-110">**Send Port Properties: General**</span></span>|<span data-ttu-id="d3483-111">傳送管線</span><span class="sxs-lookup"><span data-stu-id="d3483-111">Send pipeline</span></span>|<span data-ttu-id="d3483-112">AS2Send</span><span class="sxs-lookup"><span data-stu-id="d3483-112">AS2Send</span></span>|  
|<span data-ttu-id="d3483-113">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="d3483-113">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="d3483-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d3483-114">Property</span></span>|<span data-ttu-id="d3483-115">EdiIntAS.IsAS2AsynchronousMdn</span><span class="sxs-lookup"><span data-stu-id="d3483-115">EdiIntAS.IsAS2AsynchronousMdn</span></span>|  
|<span data-ttu-id="d3483-116">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="d3483-116">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="d3483-117">運算子</span><span class="sxs-lookup"><span data-stu-id="d3483-117">Operator</span></span>|==|  
|<span data-ttu-id="d3483-118">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="d3483-118">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="d3483-119">值</span><span class="sxs-lookup"><span data-stu-id="d3483-119">Value</span></span>|<span data-ttu-id="d3483-120">True</span><span class="sxs-lookup"><span data-stu-id="d3483-120">True</span></span>|  
  
 <span data-ttu-id="d3483-121">非同步 MDN 應傳送中包含的位址至**回條傳遞選項**收到的 AS2 訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="d3483-121">An asynchronous MDN should be sent to the address contained in the **Receipt-Delivery-Option** header of the received AS2 message.</span></span> <span data-ttu-id="d3483-122">動態傳送埠會這樣做，然而靜態傳送埠將訊息傳送到**目的地 URL**傳送連接埠定義中。</span><span class="sxs-lookup"><span data-stu-id="d3483-122">A dynamic send port will do so, whereas a static send port will send the message to the **Destination URL** in the send port definition.</span></span> <span data-ttu-id="d3483-123">這個例外狀況是如果**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性設定**驗證**單向協議索引標籤的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d3483-123">The exception to this is if the **Use agreement settings for validation and MDN instead of message header** property is set in **Validation** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="d3483-124">在此情況下，傳送埠將 MDN 訊息傳送至的 URL 輸入到**回條傳遞選項**協議屬性。</span><span class="sxs-lookup"><span data-stu-id="d3483-124">In that case, the send port will send the MDN message to the URL entered into the **Receipt-Delivery-Option** agreement property.</span></span> <span data-ttu-id="d3483-125">不過，用來執行這項處理的傳送埠仍然必須屬於動態傳送埠，而不能是靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d3483-125">However, the send port used to do so must still be a dynamic send port, not a static send port.</span></span>  
  
 <span data-ttu-id="d3483-126">您可以設定這個傳送埠，使 MDN 和 EDI 通知都可傳回。</span><span class="sxs-lookup"><span data-stu-id="d3483-126">You can configure this send port to return both MDNs and EDI acknowledgments.</span></span> <span data-ttu-id="d3483-127">在這個執行個體中，如果 EDIINT/AS2 編碼訊息已成功透過 HTTP/HTTPS 完成傳輸，但是 EDI 編碼內容的處理作業失敗，這時原始訊息的傳送者將會同時收到 MDN 和 EDI 通知，前者指出 AS2 處理成功，後者則指出 EDI 處理失敗。</span><span class="sxs-lookup"><span data-stu-id="d3483-127">In the instance, if an EDIINT/AS2-encoded message is transported over HTTP/HTTPS successfully, but processing of the EDI-encoded payload fails, the sender of the original message would receive both an MDN indicating successful AS2 processing and an EDI acknowledgment indicating a failure in EDI processing.</span></span> <span data-ttu-id="d3483-128">系統將會擱置 EDI 編碼內容，並發佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3483-128">The EDI-encoded payload would be suspended and an error posted.</span></span>  
  
## <a name="functionality"></a><span data-ttu-id="d3483-129">功能</span><span class="sxs-lookup"><span data-stu-id="d3483-129">Functionality</span></span>  
 <span data-ttu-id="d3483-130">傳送埠和管線必須執行下列動作，才能傳送 MDN：</span><span class="sxs-lookup"><span data-stu-id="d3483-130">The send port and pipeline must do the following to send an MDN:</span></span>  
  
-   <span data-ttu-id="d3483-131">根據 `EdiIntAS.IsAS2AsynchronousMdn==True` 屬性進行篩選，以便收取該 MDN。</span><span class="sxs-lookup"><span data-stu-id="d3483-131">Pick up the MDN by filtering on the `EdiIntAS.IsAS2AsynchronousMdn==True` property.</span></span>  
  
-   <span data-ttu-id="d3483-132">建置 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d3483-132">Build an AS2 message.</span></span> <span data-ttu-id="d3483-133">如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="d3483-133">For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
-   <span data-ttu-id="d3483-134">中的位址，將 MDN 路由**回條傳遞選項**訊息標頭中的一行。</span><span class="sxs-lookup"><span data-stu-id="d3483-134">Route the MDN to the address in the **Receipt-Delivery-Option** line in the header of the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3483-135">如果**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性設定**驗證**單向協議索引標籤的頁面**協議屬性**對話方塊中，傳送埠將 MDN 訊息傳送至的 URL 輸入到**回條傳遞選項**協議屬性，而不以解決**回條傳遞選項**收到的 AS2 訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="d3483-135">If the **Use agreement settings for validation and MDN instead of message header** property is set in **Validation** page of the one-way agreement tab of the **Agreement Properties** dialog box, the send port will send the MDN message to the URL entered into the **Receipt-Delivery-Option** agreement property, not to the address mentioned in **Receipt-Delivery-Option** header of the received AS2 message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3483-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3483-136">See Also</span></span>  
 [<span data-ttu-id="d3483-137">設定 AS2 方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="d3483-137">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)