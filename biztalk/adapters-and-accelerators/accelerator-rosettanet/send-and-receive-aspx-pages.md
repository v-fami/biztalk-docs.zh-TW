---
title: "傳送和接收 ASPX 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, ASPX pages
- ASPX pages, initiator
- HTTP adapters
- connections, HTTP adapters
- connections, single-action
- ASPX pages, responder
- single-action connections
- RNIFSend.aspx
- connections, asynchronous
- ASPX pages, about ASPX pages
- double-action connections
- connections, synchronous
- connections, double-action
- ASPX pages
- HTTP adapters, connections
- asynchronous connections
- RNIFReceive.aspx
- synchronous connections
ms.assetid: 21e52390-35d8-44b1-a5cd-1cd60cfe6e61
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0782c421dfe771cd024b5ce4df893e2aaa45721d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="send-and-receive-aspx-pages"></a><span data-ttu-id="cff3c-102">傳送和接收 ASPX 頁面</span><span class="sxs-lookup"><span data-stu-id="cff3c-102">Send and Receive ASPX Pages</span></span>
<span data-ttu-id="cff3c-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] ASPX 頁面是之間的直接介面[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]和網際網路。</span><span class="sxs-lookup"><span data-stu-id="cff3c-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] ASPX pages are the direct interfaces between [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] and the Internet.</span></span> <span data-ttu-id="cff3c-104">ASPX 頁面有兩種，分別是接收頁面 (RNIFReceive.aspx) 和傳送頁面 (RNIFSend.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cff3c-104">The two ASPX pages are the receive page (RNIFReceive.aspx) and the send page (RNIFSend.aspx).</span></span> <span data-ttu-id="cff3c-105">每個 ASPX 頁面都是對應的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管線的延伸。</span><span class="sxs-lookup"><span data-stu-id="cff3c-105">Each ASPX page is an extension to the corresponding [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline.</span></span> <span data-ttu-id="cff3c-106">管線需要 ASPX 頁面才能處理 RosettaNet 實作架構 (RNIF) 標頭。</span><span class="sxs-lookup"><span data-stu-id="cff3c-106">The pipeline requires the ASPX page to handle RosettaNet Implementation Framework (RNIF) headers.</span></span> <span data-ttu-id="cff3c-107">管線執行大多數的 HTTP 處理，然而，每個 ASPX 頁面執行 RNIF 標頭的 HTTP 處理。</span><span class="sxs-lookup"><span data-stu-id="cff3c-107">The pipeline performs most of the HTTP processing; however, each ASPX page performs the HTTP processing of the RNIF headers.</span></span> <span data-ttu-id="cff3c-108">頁面能夠擴大 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="cff3c-108">The pages augment the functionality in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] HTTP adapter.</span></span>  
  
 <span data-ttu-id="cff3c-109">每個 ASPX 頁面都是 ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web 應用程式，但不具有使用者介面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-109">Each ASPX page is an ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web application with no user interface.</span></span> <span data-ttu-id="cff3c-110">這些頁面使用 ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web 安全性以確保與外部合作對象建立安全連線。</span><span class="sxs-lookup"><span data-stu-id="cff3c-110">They use ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web security to ensure a secure connection with external parties.</span></span> <span data-ttu-id="cff3c-111">您可以在所提供的階層中實作容錯、延展性以及高可用性的服務。</span><span class="sxs-lookup"><span data-stu-id="cff3c-111">They provide a layer in which you can implement fault tolerance, scalability, and highly available services.</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="cff3c-112"> 安裝程式會在每個 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 部署中安裝 RNIFSend.aspx 頁面和 RNIFReceive.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-112"> setup installs an RNIFSend.aspx page and an RNIFReceive.aspx page on each deployment of [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="cff3c-113">當啟動者或是回應者與交易夥伴交換訊息時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用 ASPX 頁面傳送或接收來自交易夥伴 URL 的訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-113">When the initiator or responder exchanges messages with the trading partner, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the ASPX pages to send messages to, or receive messages from, the partner URL.</span></span> <span data-ttu-id="cff3c-114">如果啟動者和回應者都使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，則啟動者的兩個 ASPX 頁面就會與回應者的兩個 ASPX 頁面交換訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-114">If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the two ASPX pages on the initiator exchange messages with the two ASPX pages on the responder.</span></span> <span data-ttu-id="cff3c-115">如需詳細資訊，請參閱下列的＜啟動者端和回應者端 ASPX 頁面的互動方式＞一節。</span><span class="sxs-lookup"><span data-stu-id="cff3c-115">For more information, see the "How Initiator and Responder ASPX Pages Interact" subsection below.</span></span>  
  
## <a name="send-aspx-page"></a><span data-ttu-id="cff3c-116">ASPX 傳送頁面</span><span class="sxs-lookup"><span data-stu-id="cff3c-116">Send ASPX Page</span></span>  
 <span data-ttu-id="cff3c-117">RNIFSend.aspx 頁面會接收來自 BizTalk HTTP 配接器的訊息，</span><span class="sxs-lookup"><span data-stu-id="cff3c-117">The RNIFSend.aspx page receives a message from the BizTalk HTTP adapter.</span></span> <span data-ttu-id="cff3c-118">建立 RNIF 標頭並新增至訊息中，然後透過網際網路傳送訊息給交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="cff3c-118">It creates and adds RNIF headers to the message, and then sends the message to the partner over the Internet.</span></span> <span data-ttu-id="cff3c-119">HTTP 配接器使用下列命令呼叫 RNIFSend.aspx：</span><span class="sxs-lookup"><span data-stu-id="cff3c-119">The HTTP adapter calls RNIFSend.aspx with the following command:</span></span>  
  
```  
http://localhost:<port number>/RNIFSend.aspx?<query string>  
```  
  
 <span data-ttu-id="cff3c-120">查詢字串包括了傳送頁面將訊息傳送給交易夥伴時所需的下列資料，以及交易夥伴處理訊息時所需具備的資料：</span><span class="sxs-lookup"><span data-stu-id="cff3c-120">The query string includes the following data that the send page needs to send the message to the partner, and the data that the partner must have to process the message:</span></span>  
  
-   <span data-ttu-id="cff3c-121">交易夥伴 URL: http://www。\<*位址*\>.com/RNIFReceive.aspx</span><span class="sxs-lookup"><span data-stu-id="cff3c-121">The trading-partner URL: http://www.\<*address*\>.com/RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="cff3c-122">回應類型： sync 或 async</span><span class="sxs-lookup"><span data-stu-id="cff3c-122">The response type: sync or async</span></span>  
  
-   <span data-ttu-id="cff3c-123">RNIF 版本： 1.1 或 2.0。</span><span class="sxs-lookup"><span data-stu-id="cff3c-123">The RNIF version: 1.1 or 2.0.</span></span>  
  
 <span data-ttu-id="cff3c-124">BizTalk HTTP 配接器會將 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線所產生的 MIME 訊息傳送至啟動者的 RNIFSend.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-124">The BizTalk HTTP adapter sends a MIME message produced by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline to the initiator RNIFSend.aspx page.</span></span> <span data-ttu-id="cff3c-125">RNIFSend.aspx 會依照下列方式處理訊息：</span><span class="sxs-lookup"><span data-stu-id="cff3c-125">RNIFSend.aspx processes the message as follows:</span></span>  
  
1.  <span data-ttu-id="cff3c-126">傳送頁面執行訊息的驗證。</span><span class="sxs-lookup"><span data-stu-id="cff3c-126">The send page performs validation on the message.</span></span>  
  
2.  <span data-ttu-id="cff3c-127">傳送頁面根據內容類型、長度、識別碼以及 MIME 版本，建立多用途網際網路郵件延伸標準 (MIME) 標頭。</span><span class="sxs-lookup"><span data-stu-id="cff3c-127">The send page creates a Multipurpose Internet Mail Extensions (MIME) header based upon the content type, the length, the ID, and the MIME version.</span></span> <span data-ttu-id="cff3c-128">它會將 MIME 標頭及 MIME 上下界限新增至訊息中。</span><span class="sxs-lookup"><span data-stu-id="cff3c-128">It adds the MIME header, and upper and lower MIME boundaries, to the message.</span></span>  
  
3.  <span data-ttu-id="cff3c-129">對於 RNIF 2.01，傳送頁面會依照下列方式設定 HTTP 標頭的屬性：</span><span class="sxs-lookup"><span data-stu-id="cff3c-129">For RNIF 2.01, the send page sets properties of the HTTP header as follows:</span></span>  
  
    1.  <span data-ttu-id="cff3c-130">將 X-RN-Version 屬性設為在程序組態設定的 Version 屬性中輸入的版本。</span><span class="sxs-lookup"><span data-stu-id="cff3c-130">It sets the X-RN-Version property to the version entered in the Version property of the process configuration settings.</span></span>  
  
    2.  <span data-ttu-id="cff3c-131">將 X-RN-ResponseType 屬性設為 sync (同步) 或 async (非同步)，視程序組態設定中 IsSynchronous 屬性的設定而定。</span><span class="sxs-lookup"><span data-stu-id="cff3c-131">It sets the X-RN-ResponseType property to either sync or async, depending upon the setting of the IsSynchronous property in the process configuration settings.</span></span>  
  
    3.  <span data-ttu-id="cff3c-132">將 Content-Length 屬性設為完整訊息的大小。</span><span class="sxs-lookup"><span data-stu-id="cff3c-132">It sets the Content-Length property to the size of the full message.</span></span>  
  
4.  <span data-ttu-id="cff3c-133">傳送頁面根據交易夥伴協議中的「動作 URL」或「信號 URL」設定，使用 HTTP Post 傳送訊息到交易夥伴的目的地 URL。</span><span class="sxs-lookup"><span data-stu-id="cff3c-133">Using an HTTP Post, the send page sends the message to the partner's destination URL, as set in the Action URL or Signal URL settings in the trading partner agreement.</span></span>  
  
5.  <span data-ttu-id="cff3c-134">傳送頁面等候 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="cff3c-134">The send page waits for the HTTP response.</span></span> <span data-ttu-id="cff3c-135">一旦收到回應，便將回應傳送至 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="cff3c-135">When it receives the response, it routes it to the HTTP adapter.</span></span>  
  
6.  <span data-ttu-id="cff3c-136">如果連線是非同步，傳送頁面會關閉連線，並且它的處理隨即完成。</span><span class="sxs-lookup"><span data-stu-id="cff3c-136">If the connection is asynchronous, the send page closes the connection, and its processing is complete.</span></span>  
  
7.  <span data-ttu-id="cff3c-137">如果連線是同步，傳送頁面會保持連線開啟以取得回傳訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-137">If the connection is synchronous, the send page keeps the connection open for a returned message.</span></span> <span data-ttu-id="cff3c-138">在收到訊息之後，傳送頁面會如同 RNIFReceive.aspx 頁面處理所接收訊息的方式處理訊息，並傳送接收的訊息至 HTTP 配接器，然後關閉連線。</span><span class="sxs-lookup"><span data-stu-id="cff3c-138">After it receives the message, it performs the same processing that an RNIFReceive.aspx page performs on a received message, sends the received message to the HTTP adapter, and then closes the connection.</span></span>  
  
## <a name="receive-aspx-page"></a><span data-ttu-id="cff3c-139">ASPX 接收頁面</span><span class="sxs-lookup"><span data-stu-id="cff3c-139">Receive ASPX Page</span></span>  
 <span data-ttu-id="cff3c-140">RNIFReceive.aspx 頁面透過網際網路接收來自交易夥伴的 HTTP 訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-140">The RNIFReceive.aspx page receives an HTTP message from the partner over the Internet.</span></span> <span data-ttu-id="cff3c-141">它會處理、驗證然後移除 RNIF 標頭，再將訊息提交至 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="cff3c-141">It processes, validates, and then removes the RNIF headers, and submits the message to the HTTP adapter.</span></span> <span data-ttu-id="cff3c-142">接收頁面所接收的訊息必須符合 RNIF HTTP 傳輸格式。</span><span class="sxs-lookup"><span data-stu-id="cff3c-142">The message received by the receive page must be RNIF HTTP transport-compliant.</span></span> <span data-ttu-id="cff3c-143">接收頁面會依照下列方式處理訊息：</span><span class="sxs-lookup"><span data-stu-id="cff3c-143">The receive page processes messages as follows:</span></span>  
  
1.  <span data-ttu-id="cff3c-144">回應者的 RNIFReceive.aspx 頁面接收來自啟動者的訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-144">The responder RNIFReceive.aspx page receives the message from the initiator.</span></span> <span data-ttu-id="cff3c-145">訊息包含 MIME 標頭以及上下界限。</span><span class="sxs-lookup"><span data-stu-id="cff3c-145">The message contains the MIME header and upper and lower boundaries.</span></span>  
  
2.  <span data-ttu-id="cff3c-146">接收頁面驗證 MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="cff3c-146">The receive page validates the MIME header.</span></span>  
  
3.  <span data-ttu-id="cff3c-147">接收頁面從訊息中移除 MIME 標頭及界限。</span><span class="sxs-lookup"><span data-stu-id="cff3c-147">The receive page removes the MIME header and boundaries from the message.</span></span>  
  
4.  <span data-ttu-id="cff3c-148">接收頁面使用 HTTP 接收位置張貼訊息至 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="cff3c-148">The receive page posts the message to the HTTP adapter using the HTTP receive location.</span></span> <span data-ttu-id="cff3c-149">接收頁面接收 HTTP 回應，然後回傳 HTTP 回應至啟動者的傳送頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-149">The receive page receives an HTTP response, and returns the HTTP response to the send page of the initiator.</span></span>  
  
5.  <span data-ttu-id="cff3c-150">如果連線是非同步的，接收頁面會關閉連線。</span><span class="sxs-lookup"><span data-stu-id="cff3c-150">If the connection is asynchronous, the receive page closes the connection.</span></span>  
  
6.  <span data-ttu-id="cff3c-151">如果連線是同步的，接收頁面會保持連線開啟，等待回傳的訊息。</span><span class="sxs-lookup"><span data-stu-id="cff3c-151">If the connection is synchronous, the receive page keeps the connection open, waiting for a returned message.</span></span>  
  
7.  <span data-ttu-id="cff3c-152">在收到 HTTP 配接器回傳的訊息之後，接收頁面處理訊息的方式將如同 RNIFSend.aspx 頁面，並傳送回傳的訊息至啟動者的傳送頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-152">After it receives the returned message from the HTTP adapter, the receive page performs the same processing that an RNIFSend.aspx page does, and sends the returned message to the initiator send page.</span></span> <span data-ttu-id="cff3c-153">一旦收到 HTTP 回應之後，隨即關閉連線。</span><span class="sxs-lookup"><span data-stu-id="cff3c-153">After it receives the HTTP response, it closes the connection.</span></span>  
  
## <a name="how-initiator-and-responder-aspx-pages-interact"></a><span data-ttu-id="cff3c-154">啟動者端和回應者端 ASPX 頁面的互動方式</span><span class="sxs-lookup"><span data-stu-id="cff3c-154">How Initiator and Responder ASPX Pages Interact</span></span>  
 <span data-ttu-id="cff3c-155">如果啟動者和回應者都使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，啟動者端和回應者端的四個 ASPX 頁面會根據連線是同步或非同步、訊息是單向動作或雙向動作而採用不同的方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="cff3c-155">If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the four ASPX pages on the initiator and responder interact differently depending on whether the connections are asynchronous or synchronous, and whether the messages are single-action or double-action.</span></span> <span data-ttu-id="cff3c-156">下列各節詳細描述完整的互動方式。</span><span class="sxs-lookup"><span data-stu-id="cff3c-156">The following subsections describe the complete set of interactions.</span></span>  
  
 <span data-ttu-id="cff3c-157">**雙向動作非同步**</span><span class="sxs-lookup"><span data-stu-id="cff3c-157">**Double-Action Asynchronous**</span></span>  
  
 <span data-ttu-id="cff3c-158">此實例牽涉四個不同的 HTTP 連線，每個步驟說明一個連線：</span><span class="sxs-lookup"><span data-stu-id="cff3c-158">This scenario involves four separate HTTP connections, one for each step:</span></span>  
  
1.  <span data-ttu-id="cff3c-159">啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-159">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cff3c-160">下列的步驟 2 和 3 可能需要以相反的順序執行，視系統的負載程度而定。</span><span class="sxs-lookup"><span data-stu-id="cff3c-160">Steps 2 and 3 below may occur in the reverse order, depending upon system load.</span></span>  
  
2.  <span data-ttu-id="cff3c-161">回應者傳送頁面傳送要求信號訊息給啟動者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-161">The responder send page sends a request signal message to the initiator receive page.</span></span>  
  
3.  <span data-ttu-id="cff3c-162">回應者傳送頁面傳送動作回應訊息給啟動者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-162">The responder send page sends an action response message to the initiator receive page.</span></span>  
  
4.  <span data-ttu-id="cff3c-163">啟動者傳送頁面傳送回應信號訊息給回應者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-163">The initiator send page sends a response signal message to the responder receive page.</span></span>  
  
 <span data-ttu-id="cff3c-164">**單向動作非同步**</span><span class="sxs-lookup"><span data-stu-id="cff3c-164">**Single-Action Asynchronous**</span></span>  
  
 <span data-ttu-id="cff3c-165">此實例牽涉兩個不同的 HTTP 連線，每個步驟說明一個連線。</span><span class="sxs-lookup"><span data-stu-id="cff3c-165">This scenario involves two separate HTTP connections, one for each step.</span></span> <span data-ttu-id="cff3c-166">請注意，此實例是由雙向動作非同步實例的步驟 1 和 2 組成。</span><span class="sxs-lookup"><span data-stu-id="cff3c-166">Note that this scenario consists of step 1 and 2 of the double-action asynchronous scenario.</span></span>  
  
1.  <span data-ttu-id="cff3c-167">啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-167">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="cff3c-168">回應者傳送頁面傳送要求信號訊息給啟動者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-168">The responder send page sends a request signal message to the initiator receive page.</span></span>  
  
 <span data-ttu-id="cff3c-169">**雙向動作同步**</span><span class="sxs-lookup"><span data-stu-id="cff3c-169">**Double-Action Synchronous**</span></span>  
  
 <span data-ttu-id="cff3c-170">此實例牽涉一個 HTTP 連線：</span><span class="sxs-lookup"><span data-stu-id="cff3c-170">This scenario involves one HTTP connection:</span></span>  
  
1.  <span data-ttu-id="cff3c-171">啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-171">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="cff3c-172">回應者接收頁面透過步驟 1 所使用的相同連線傳送動作回應訊息 (如果有問題的話，會傳送例外狀況) 至啟動者傳送頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-172">The responder receive page sends an action response message (or an exception, if there is a problem) to the initiator send page on the same connection used in step 1.</span></span>  
  
 <span data-ttu-id="cff3c-173">**單向動作同步**</span><span class="sxs-lookup"><span data-stu-id="cff3c-173">**Single-Action Synchronous**</span></span>  
  
 <span data-ttu-id="cff3c-174">此實例牽涉一個 HTTP 連線：</span><span class="sxs-lookup"><span data-stu-id="cff3c-174">This scenario involves one HTTP connection:</span></span>  
  
1.  <span data-ttu-id="cff3c-175">啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-175">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="cff3c-176">回應者接收頁面透過相同連線傳送要求信號訊息 (如果有問題的話，會傳送例外狀況) 至啟動者傳送頁面。</span><span class="sxs-lookup"><span data-stu-id="cff3c-176">The responder receive page sends a request signal message (or an exception, if there is a problem) to the initiator send page on the same connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff3c-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="cff3c-177">See Also</span></span>  
 <span data-ttu-id="cff3c-178">[BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="cff3c-178">[Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md) </span></span>  
 <span data-ttu-id="cff3c-179">[BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="cff3c-179">[BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span></span>  
 [<span data-ttu-id="cff3c-180">BTARN 傳送管線</span><span class="sxs-lookup"><span data-stu-id="cff3c-180">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)