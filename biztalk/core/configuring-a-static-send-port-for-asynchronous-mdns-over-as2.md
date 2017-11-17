---
title: "設定透過 AS2 之非同步 Mdn 的靜態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc43e767-d9d7-4b02-b3fc-0cfdfd6e61c4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ccae5741ada6db57538289911a97e2ad3d9dfce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-static-send-port-for-asynchronous-mdns-over-as2"></a><span data-ttu-id="6e7a1-102">設定透過 AS2 之非同步 MDN 的靜態傳送埠</span><span class="sxs-lookup"><span data-stu-id="6e7a1-102">Configuring a Static Send Port for Asynchronous MDNs over AS2</span></span>
<span data-ttu-id="6e7a1-103">本主題說明如何設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使其透過靜態傳送埠傳送非同步 EDIINT/AS2 編碼 MDN 訊息。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send an asynchronous EDIINT/AS2-encoded MDN message over a static send port.</span></span> <span data-ttu-id="6e7a1-104">進行這項設定時必須建立靜態傳送埠，若有必要，也須設定供傳送埠使用的加密憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-104">This configuration includes creating the static send port and if required, setting up an encryption certificate to be used by the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e7a1-105">您可以設定動態傳送埠傳送 MDN 訊息，而不使用靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-105">You can configure a dynamic send port to send MDN messages, instead of a static send port.</span></span> <span data-ttu-id="6e7a1-106">如需詳細資訊，請參閱[設定透過 AS2 之非同步 Mdn 的動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-106">For more information, see [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).</span></span>  
  
 <span data-ttu-id="6e7a1-107">若要傳送 MDN 訊息，請以下列組態建立單向 HTTP 傳送埠：</span><span class="sxs-lookup"><span data-stu-id="6e7a1-107">To send an MDN message, create a one-way HTTP send port with the following configuration:</span></span>  
  
|<span data-ttu-id="6e7a1-108">位置</span><span class="sxs-lookup"><span data-stu-id="6e7a1-108">Location</span></span>|<span data-ttu-id="6e7a1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6e7a1-109">Property</span></span>|<span data-ttu-id="6e7a1-110">設定</span><span class="sxs-lookup"><span data-stu-id="6e7a1-110">Setting</span></span>|  
|--------------|--------------|-------------|  
|<span data-ttu-id="6e7a1-111">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-111">**Send Port Properties: General**</span></span>|<span data-ttu-id="6e7a1-112">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="6e7a1-112">Port Type</span></span>|<span data-ttu-id="6e7a1-113">靜態單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="6e7a1-113">Static One-way Send Port</span></span>|  
|<span data-ttu-id="6e7a1-114">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-114">**Send Port Properties: General**</span></span>|<span data-ttu-id="6e7a1-115">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="6e7a1-115">Transport Type</span></span>|<span data-ttu-id="6e7a1-116">HTTP**附註：**只有 HTTP 配接器可以用於傳輸 EDIINT/AS2 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-116">HTTP **Note:**  Only the HTTP adapter can be used for transporting EDIINT/AS2-encoded messages.</span></span> <span data-ttu-id="6e7a1-117">這種傳輸無法搭配 HTTP 配接器以外的配接器運作。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-117">This transport will not work with an adapter other than the HTTP adapter.</span></span>|  
|<span data-ttu-id="6e7a1-118">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-118">**Send Port Properties: General**</span></span>|<span data-ttu-id="6e7a1-119">傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="6e7a1-119">Send handler</span></span>|<span data-ttu-id="6e7a1-120">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="6e7a1-120">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="6e7a1-121">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-121">**Send Port Properties: General**</span></span>|<span data-ttu-id="6e7a1-122">傳送管線</span><span class="sxs-lookup"><span data-stu-id="6e7a1-122">Send pipeline</span></span>|<span data-ttu-id="6e7a1-123">AS2Send</span><span class="sxs-lookup"><span data-stu-id="6e7a1-123">AS2Send</span></span>|  
|<span data-ttu-id="6e7a1-124">**HTTP 傳輸屬性**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-124">**HTTP Transport Properties**</span></span>|<span data-ttu-id="6e7a1-125">目的地 URL</span><span class="sxs-lookup"><span data-stu-id="6e7a1-125">Destination URL</span></span>|<span data-ttu-id="6e7a1-126">\<目的地 URL 字串 ></span><span class="sxs-lookup"><span data-stu-id="6e7a1-126">\<Destination URL string></span></span>|  
|<span data-ttu-id="6e7a1-127">**HTTP 傳輸屬性**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-127">**HTTP Transport Properties**</span></span>|<span data-ttu-id="6e7a1-128">啟用區塊編碼</span><span class="sxs-lookup"><span data-stu-id="6e7a1-128">Enable chunked encoding</span></span>|<span data-ttu-id="6e7a1-129">已清除</span><span class="sxs-lookup"><span data-stu-id="6e7a1-129">Cleared</span></span>|  
|<span data-ttu-id="6e7a1-130">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-130">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="6e7a1-131">屬性</span><span class="sxs-lookup"><span data-stu-id="6e7a1-131">Property</span></span>|<span data-ttu-id="6e7a1-132">EdiIntAS.IsAS2AsynchronousMdn**附註：**您也應該指定額外的篩選運算式，以確保只有中指定之位址為目標的 MDN 訊息傳送埠所拾取此訂用帳戶篩選。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-132">EdiIntAS.IsAS2AsynchronousMdn **Note:**  You should also specify additional filter expressions to ensure that only MDN messages destined to the address specified in this send port are picked up by this subscription filter.</span></span>|  
|<span data-ttu-id="6e7a1-133">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-133">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="6e7a1-134">運算子</span><span class="sxs-lookup"><span data-stu-id="6e7a1-134">Operator</span></span>|==|  
|<span data-ttu-id="6e7a1-135">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-135">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="6e7a1-136">值</span><span class="sxs-lookup"><span data-stu-id="6e7a1-136">Value</span></span>|<span data-ttu-id="6e7a1-137">True</span><span class="sxs-lookup"><span data-stu-id="6e7a1-137">True</span></span>|  
|<span data-ttu-id="6e7a1-138">**傳送埠屬性： 憑證**</span><span class="sxs-lookup"><span data-stu-id="6e7a1-138">**Send Port Properties: Certificates**</span></span>|<span data-ttu-id="6e7a1-139">一般名稱和指紋</span><span class="sxs-lookup"><span data-stu-id="6e7a1-139">Common Name  and thumbprint</span></span>|<span data-ttu-id="6e7a1-140">如果對外寄 MDN 訊息使用加密憑證，請輸入憑證名稱和指紋。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-140">Enter the certificate name and thumbprint if using an encryption certificate for the outbound MDN message.</span></span>|  
  
 <span data-ttu-id="6e7a1-141">非同步 MDN 應傳送至中指定的位址**回條傳遞選項**收到的 AS2 訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-141">An asynchronous MDN should be sent to the address specified in the **Receipt-Delivery-Option** header of the received AS2 message.</span></span> <span data-ttu-id="6e7a1-142">動態傳送埠將會自動執行這個動作，而靜態傳送埠將訊息傳送到**目的地 URL**的傳送埠屬性中。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-142">A dynamic send port will do so automatically, whereas a static send port will send the message to the **Destination URL** in the send port properties.</span></span> <span data-ttu-id="6e7a1-143">使用靜態傳送埠傳送非同步 MDN 時，請確定要傳送的目標 URL 正確無誤。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-143">When sending an asynchronous MDN with a static send port, ensure that the URL you are sending to is correct.</span></span>  
  
## <a name="functionality"></a><span data-ttu-id="6e7a1-144">功能</span><span class="sxs-lookup"><span data-stu-id="6e7a1-144">Functionality</span></span>  
 <span data-ttu-id="6e7a1-145">傳送埠和管線必須執行下列動作，才能傳送 MDN：</span><span class="sxs-lookup"><span data-stu-id="6e7a1-145">The send port and pipeline must do the following to send an MDN:</span></span>  
  
-   <span data-ttu-id="6e7a1-146">根據 `EdiIntAS.IsAS2AsynchronousMdn==True` 屬性進行篩選，以便收取該 MDN。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-146">Pick up the MDN by filtering on the `EdiIntAS.IsAS2AsynchronousMdn==True` property.</span></span>  
  
-   <span data-ttu-id="6e7a1-147">建置 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-147">Build an AS2 message.</span></span> <span data-ttu-id="6e7a1-148">如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-148">For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
-   <span data-ttu-id="6e7a1-149">將 MDN 路由傳送至傳送埠中定義的位址。</span><span class="sxs-lookup"><span data-stu-id="6e7a1-149">Route the MDN to the address defined in the send port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7a1-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e7a1-150">See Also</span></span>  
 [<span data-ttu-id="6e7a1-151">設定 AS2 方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="6e7a1-151">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)