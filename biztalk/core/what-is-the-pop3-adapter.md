---
title: 何謂 POP3 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- POP3 adapters, availability
- authenticating, POP3 adapters
- POP3 adapters, data duplication
- data duplication
- POP3 adapters, receive adapters
- high availability, POP3 adapters
- POP3 adapters, supported platforms
- POP3 adapters, authenticating
- POP3 adapters, algorithims
- receive adapters, POP3 adapters
ms.assetid: 05e9598b-cdfe-4216-b6bf-1b84f8ddfeae
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa0f4679cb898f9ce2c4008505bd1ec4a2540dab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974327"
---
# <a name="what-is-the-pop3-adapter"></a><span data-ttu-id="8b722-103">何謂 POP3 配接器？</span><span class="sxs-lookup"><span data-stu-id="8b722-103">What Is the POP3 Adapter?</span></span>
<span data-ttu-id="8b722-104">本節說明 POP3 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="8b722-104">This section describes the POP3 receive adapter.</span></span>  
  
## <a name="pop3-receive-adapter"></a><span data-ttu-id="8b722-105">POP3 接收配接器</span><span class="sxs-lookup"><span data-stu-id="8b722-105">POP3 Receive Adapter</span></span>  
 <span data-ttu-id="8b722-106">POP3 接收配接器可讓您將資料從啟用 POP3 的信箱移到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="8b722-106">The POP3 receive adapter enables you to move data from a POP3-enabled mailbox to BizTalk Server.</span></span>  
  
 <span data-ttu-id="8b722-107">POP3 接收配接器的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="8b722-107">The key features of the POP3 receive adapter are:</span></span>  
  
-   <span data-ttu-id="8b722-108">依需要從 POP3 伺服器信箱提取檔案。</span><span class="sxs-lookup"><span data-stu-id="8b722-108">Pulling files from the POP3 server mailbox on demand.</span></span>  
  
-   <span data-ttu-id="8b722-109">根據可設定的排程執行輪詢。</span><span class="sxs-lookup"><span data-stu-id="8b722-109">Running polls based on a configurable schedule.</span></span>  
  
-   <span data-ttu-id="8b722-110">輪詢 POP3 伺服器信箱並直接將資料傳送到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="8b722-110">Polling the POP3 server mailbox and sending data directly to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="8b722-111">將 POP3 伺服器信箱指定為 IP 位址或主控件名稱、連接埠、使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8b722-111">Specifying the POP3 server mailbox as an IP address or host name, port, user name, and password.</span></span>  
  
-   <span data-ttu-id="8b722-112">能夠從需要「安全通訊端層」(SSL) 連線的郵件伺服器下載電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8b722-112">Ability to download e-mail from mail servers that require Secure Sockets Layer (SSL) connections.</span></span>  
  
-   <span data-ttu-id="8b722-113">保證傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="8b722-113">Guaranteed file delivery.</span></span>  
  
-   <span data-ttu-id="8b722-114">隱含的 MIME 處理。</span><span class="sxs-lookup"><span data-stu-id="8b722-114">Implicit MIME processing.</span></span> <span data-ttu-id="8b722-115">您不需要使用 POP3 配接器時，接收管線中使用 MIME 解碼器。</span><span class="sxs-lookup"><span data-stu-id="8b722-115">It is not necessary to use a MIME decoder in a receive pipeline when using the POP3 adapter.</span></span>  
  
## <a name="pop3-adapter-supported-platforms"></a><span data-ttu-id="8b722-116">POP3 配接器支援的平台</span><span class="sxs-lookup"><span data-stu-id="8b722-116">POP3 Adapter Supported Platforms</span></span>  
 <span data-ttu-id="8b722-117">POP3 配接器的設計是要使用符合以下 RFC 的任何 POP3 伺服器：</span><span class="sxs-lookup"><span data-stu-id="8b722-117">The POP3 adapter is designed to work with any POP3 servers that conform to the following RFCs:</span></span>  
  
- <span data-ttu-id="8b722-118">**RFC 1939。**</span><span class="sxs-lookup"><span data-stu-id="8b722-118">**RFC 1939.**</span></span> <span data-ttu-id="8b722-119">郵局通訊協定第 3 版 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58808 ](http://go.microsoft.com/fwlink/?LinkId=58808))</span><span class="sxs-lookup"><span data-stu-id="8b722-119">Post Office Protocol Version 3 (see [http://go.microsoft.com/fwlink/?LinkId=58808](http://go.microsoft.com/fwlink/?LinkId=58808))</span></span>  
  
- <span data-ttu-id="8b722-120">**RFC 1734。**</span><span class="sxs-lookup"><span data-stu-id="8b722-120">**RFC 1734.**</span></span> <span data-ttu-id="8b722-121">POP3 驗證命令 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58809 ](http://go.microsoft.com/fwlink/?LinkId=58809))</span><span class="sxs-lookup"><span data-stu-id="8b722-121">POP3 AUTHentication command (see [http://go.microsoft.com/fwlink/?LinkId=58809](http://go.microsoft.com/fwlink/?LinkId=58809))</span></span>  
  
- <span data-ttu-id="8b722-122">**RFC 2045。**</span><span class="sxs-lookup"><span data-stu-id="8b722-122">**RFC 2045.**</span></span> <span data-ttu-id="8b722-123">多用途網際網路郵件延伸標準 (MIME) 第一段： 格式的網際網路訊息內文 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58810 ](http://go.microsoft.com/fwlink/?LinkId=58810))</span><span class="sxs-lookup"><span data-stu-id="8b722-123">Multipurpose Internet Mail Extensions (MIME) Part One: Format of Internet Message Bodies (see [http://go.microsoft.com/fwlink/?LinkId=58810](http://go.microsoft.com/fwlink/?LinkId=58810))</span></span>  
  
- <span data-ttu-id="8b722-124">**RFC 2046。**</span><span class="sxs-lookup"><span data-stu-id="8b722-124">**RFC 2046.**</span></span> <span data-ttu-id="8b722-125">多用途網際網路郵件延伸標準 (MIME) 第二部分： 媒體類型 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58811 ](http://go.microsoft.com/fwlink/?LinkId=58811))</span><span class="sxs-lookup"><span data-stu-id="8b722-125">Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types (see [http://go.microsoft.com/fwlink/?LinkId=58811](http://go.microsoft.com/fwlink/?LinkId=58811))</span></span>  
  
- <span data-ttu-id="8b722-126">**RFC 2047。**</span><span class="sxs-lookup"><span data-stu-id="8b722-126">**RFC 2047.**</span></span> <span data-ttu-id="8b722-127">MIME （多用途網際網路郵件延伸標準） 第三部分： 非 ASCII 文字的訊息標頭延伸模組 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58812 ](http://go.microsoft.com/fwlink/?LinkId=58812))</span><span class="sxs-lookup"><span data-stu-id="8b722-127">MIME (Multipurpose Internet Mail Extensions) Part Three: Message Header Extensions for Non-ASCII Text (see [http://go.microsoft.com/fwlink/?LinkId=58812](http://go.microsoft.com/fwlink/?LinkId=58812))</span></span>  
  
  <span data-ttu-id="8b722-128">POP3 配接器已在 Microsoft Exchange Server 2003 上進行過大規模的測試。</span><span class="sxs-lookup"><span data-stu-id="8b722-128">The POP3 adapter was tested extensively against Microsoft Exchange Server 2003.</span></span>  
  
## <a name="considerations-for-preventing-data-duplication-when-using-the-pop3-adapter"></a><span data-ttu-id="8b722-129">使用 POP3 配接器避免資料重複的考量</span><span class="sxs-lookup"><span data-stu-id="8b722-129">Considerations for Preventing Data Duplication When Using the POP3 Adapter</span></span>  
 <span data-ttu-id="8b722-130">POP3 配接器不是交易式配接器，因此容易處理相同訊息的多個複本，而可能造成資料重複。</span><span class="sxs-lookup"><span data-stu-id="8b722-130">The POP3 adapter is not a transactional adapter and therefore is subject to processing multiple copies of the same message, potentially causing data duplication.</span></span> <span data-ttu-id="8b722-131">在下列實例中，POP3 配接器有可能將傳送訊息的重複複本：</span><span class="sxs-lookup"><span data-stu-id="8b722-131">It is possible that the POP3 adapter will deliver duplicate copies of a message in the following scenarios:</span></span>  
  
-   <span data-ttu-id="8b722-132">在電子郵件成功提交到 BizTalk Server 進行處理後，POP3 配接器一定會從設定為要監控的信箱中刪除電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8b722-132">The POP3 adapter always deletes e-mails from the mailbox that it is configured to monitor after the e-mail has been successfully submitted to BizTalk Server for processing.</span></span> <span data-ttu-id="8b722-133">假使 POP3 配接器從信箱擷取電子郵件，提交電子郵件到 BizTalk Server 進行處理，但無法從信箱刪除該電子郵件時，那麼 POP3 配接器下次輪詢信箱時，就會重新提交此電子郵件到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="8b722-133">If the POP3 adapter retrieves an e-mail from a mailbox, submits the e-mail to BizTalk Server for processing, and fails to delete the e-mail from the mailbox, the e-mail will be resubmitted to BizTalk Server the next time that the POP3 adapter polls the mailbox.</span></span>  
  
-   <span data-ttu-id="8b722-134">若個別 BizTalk 主控件執行個體中的 POP3 配接器之多個執行個體同時監控相同的信箱，且 POP3 伺服器允許多個並行連線到其信箱時，那麼配接器就可能傳送重複的訊息複本。</span><span class="sxs-lookup"><span data-stu-id="8b722-134">If multiple instances of the POP3 adapter in separate BizTalk Host instances are monitoring the same mailbox simultaneously and the POP3 server allows multiple concurrent connections to its mailboxes, then the adapter may deliver duplicate copies of messages.</span></span>  
  
## <a name="high-availability-for-the-pop3-adapter"></a><span data-ttu-id="8b722-135">POP3 配接器的高可用性</span><span class="sxs-lookup"><span data-stu-id="8b722-135">High Availability for the POP3 Adapter</span></span>  
 <span data-ttu-id="8b722-136">有些 POP3 伺服器允許特定信箱可以有多個並行連線。</span><span class="sxs-lookup"><span data-stu-id="8b722-136">Some POP3 servers permit multiple concurrent connections to a given mailbox.</span></span> <span data-ttu-id="8b722-137">若設定多個 POP3 配接器執行個體從這類 POP3 伺服器上的信箱擷取郵件，就會發生資料重複的情形。</span><span class="sxs-lookup"><span data-stu-id="8b722-137">If more than one instance of the POP3 adapter is configured to retrieve mail from a mailbox on such a POP3 server then data duplication can occur.</span></span> <span data-ttu-id="8b722-138">所以，您應該僅設定一個 POP3 配接器執行個體，以便從允許多個並行連線的信箱擷取郵件。</span><span class="sxs-lookup"><span data-stu-id="8b722-138">Therefore you should configure only one instance of the POP3 adapter to retrieve mail from a mailbox that permits multiple concurrent connections.</span></span>  
  
 <span data-ttu-id="8b722-139">若要為此實例中的 POP3 配接器提供容錯功能，應該只設定一個 POP3 配接器接收處理常式在叢集 BizTalk 主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="8b722-139">To provide fault tolerance for the POP3 adapter in this scenario, a single POP3 adapter receive handler should be configured to run in a clustered BizTalk Host.</span></span> <span data-ttu-id="8b722-140">如需詳細資訊，請參閱[在叢集主控件執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。</span><span class="sxs-lookup"><span data-stu-id="8b722-140">For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="authentication-warnings-when-multiple-instances-of-the-pop3-adapter-connect-to-the-same-mailbox"></a><span data-ttu-id="8b722-141">多個 POP3 配接器執行個體連接到相同信箱時的驗證警告</span><span class="sxs-lookup"><span data-stu-id="8b722-141">Authentication Warnings When Multiple Instances of the POP3 Adapter Connect to the Same Mailbox</span></span>  
 <span data-ttu-id="8b722-142">BizTalk Server 可以設定成讓多個 POP3 配接器執行個體從相同信箱擷取郵件。</span><span class="sxs-lookup"><span data-stu-id="8b722-142">BizTalk Server may be configured to have more than one instance of the POP3 adapter retrieve mail from the same mailbox.</span></span> <span data-ttu-id="8b722-143">若是這種情形，BizTalk Server 應用程式記錄中可能會產生驗證警告，因為有些 POP3 伺服器會使用鎖定機制。</span><span class="sxs-lookup"><span data-stu-id="8b722-143">In such a case, it is possible that authentication warnings may be generated in the BizTalk Server Application log because of the locking mechanism employed by some POP3 servers.</span></span> <span data-ttu-id="8b722-144">在此情形中，這些警告對 POP3 配接器的功能並不會產生影響，因此可以放心略過。</span><span class="sxs-lookup"><span data-stu-id="8b722-144">These warnings will have no impact on the POP3 adapter functionality and can be safely ignored in this scenario.</span></span>  
  
## <a name="encrypted-messages-received-by-the-pop3-adapter-that-are-sent-to-the-suspended-queue-may-be-viewable-in-clear-text"></a><span data-ttu-id="8b722-145">傳送至訊息擱置佇列且由 POP3 配接器接收的加密訊息可以純文字檢視</span><span class="sxs-lookup"><span data-stu-id="8b722-145">Encrypted Messages Received by the POP3 Adapter that are sent to the Suspended Queue may be Viewable in Clear Text</span></span>  
 <span data-ttu-id="8b722-146">您可以設定 POP3 配接器來解密數位加密的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8b722-146">You can configure the POP3 adapter to decrypt digitally encrypted e-mails.</span></span> <span data-ttu-id="8b722-147">這是藉由設定**套用 MIME 解碼**屬性設 **，則為 True**的接收位置使用 POP3 配接器。</span><span class="sxs-lookup"><span data-stu-id="8b722-147">This is done by setting the **Apply MIME Decoding** property to **True** for receive locations that use the POP3 adapter.</span></span> <span data-ttu-id="8b722-148">如果 POP3 配接器收到數位加密的電子郵件並**套用 MIME 解碼**接收位置的屬性設定為 **，則為 True**則 POP3 配接器會嘗試解密電子郵件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8b722-148">If the POP3 Adapter receives a digitally encrypted e-mail and the **Apply MIME Decoding** property for the receive location is set to **True** then the POP3 adapter attempts to decrypt the e-mail as follows:</span></span>  
  
- <span data-ttu-id="8b722-149">POP3 配接器會搜尋與用來加密電子郵件之公用憑證相符的私用憑證。</span><span class="sxs-lookup"><span data-stu-id="8b722-149">The POP3 Adapter searches for a private certificate that matches the public certificate used to encrypt the e-mail.</span></span> <span data-ttu-id="8b722-150">私用憑證必須位在伺服器的個人憑證存放區，且此伺服器正在執行 POP3 接收處理常式繫結到的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8b722-150">The private certificate must be in the Personal certificate store of the server that is running the host instance that the POP3 receive handler is bound to.</span></span>  
  
- <span data-ttu-id="8b722-151">如果 POP3 配接器找到對應的私用憑證，便會使用此私用憑證來解密電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="8b722-151">If the POP3 Adapter locates a corresponding private certificate, it uses the private certificate to decrypt the e-mail message.</span></span>  
  
- <span data-ttu-id="8b722-152">電子郵件會解密並保存到 BizTalk MessageBox。</span><span class="sxs-lookup"><span data-stu-id="8b722-152">The e-mail is decrypted and persisted to the BizTalk MessageBox.</span></span>  
  
  <span data-ttu-id="8b722-153">如果將訊息解密並保存到 BizTalk MessageBox 後訊息被擱置，將可在 BizTalk 訊息擱置佇列中以純文字檢視訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="8b722-153">If a message is suspended after being decrypted and persisted to the BizTalk MessageBox, the contents of the message will be visible in clear text in the BizTalk suspended queue.</span></span>  
  
  <span data-ttu-id="8b722-154">如果您必須阻止訊息擱置佇列中的安全訊息文字顯示，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="8b722-154">If you need to prevent the display of secure message text in the suspended queue, follow these steps:</span></span>  
  
- <span data-ttu-id="8b722-155">設定**套用 MIME 解碼**屬性設**False**使用 POP3 配接器接收位置以及具有 SMIME 管線元件的管線中解密訊息。</span><span class="sxs-lookup"><span data-stu-id="8b722-155">Set the **Apply MIME Decoding** property to **False** for receive locations that use the POP3 adapter and decrypt the message in a pipeline with the SMIME pipeline component.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="8b722-156">此方法將會讓您無法將電子郵件特定的屬性升級為訊息內容。</span><span class="sxs-lookup"><span data-stu-id="8b722-156">This approach will prevent you from being able to promote e-mail specific properties to the message context.</span></span>  
  
- <span data-ttu-id="8b722-157">如果您需要將電子郵件特定的屬性升級為訊息內容，並確保當加密的訊息路由至訊息擱置佇列時仍保持加密，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="8b722-157">If you need to promote e-mail specific properties to the message context and ensure that encrypted messages remain encrypted if they are routed to the suspended queue, follow these steps:</span></span>  
  
  -   <span data-ttu-id="8b722-158">核取選項**啟用的路由失敗訊息**包含使用 POP3 配接器的接收位置的接收埠上。</span><span class="sxs-lookup"><span data-stu-id="8b722-158">Check the option to **Enable routing for failed messages** on the receive port that houses the receive location(s) that use the POP3 adapter.</span></span>  
  
  -   <span data-ttu-id="8b722-159">建立協調流程來訂閱無法傳遞到接收埠的訊息，此接收埠包含使用 POP3 配接器的接收位置。</span><span class="sxs-lookup"><span data-stu-id="8b722-159">Create an orchestration to subscribe to messages that fail delivery to the receive port that houses the receive location(s) that use the POP3 adapter.</span></span>  
  
  -   <span data-ttu-id="8b722-160">以在管線中使用 SMIME 管線元件加密訊息的傳送埠來設定協調流程。</span><span class="sxs-lookup"><span data-stu-id="8b722-160">Configure the orchestration with a send port that encrypts the message in a pipeline using the SMIME pipeline component.</span></span>  
  
  -   <span data-ttu-id="8b722-161">以擱置圖形設定協調流程，來擱置協調流程執行個體和訊息。</span><span class="sxs-lookup"><span data-stu-id="8b722-161">Configure the orchestration with a suspend shape to suspend the orchestration instance and the message.</span></span>  
  
  -   <span data-ttu-id="8b722-162">建立和部署協調流程，將部署的協調流程繫結到適當的接收埠。</span><span class="sxs-lookup"><span data-stu-id="8b722-162">Build and deploy the orchestration, bind the deployed orchestration to the appropriate receive port.</span></span>  
  
## <a name="maximum-message-size-supported-by-the-pop3-adapter"></a><span data-ttu-id="8b722-163">POP3 配接器支援的最大訊息大小</span><span class="sxs-lookup"><span data-stu-id="8b722-163">Maximum Message Size Supported by the POP3 Adapter</span></span>  
 <span data-ttu-id="8b722-164">POP3 配接器經過測試，且可支援接收最高達 50 MB 的訊息容量。</span><span class="sxs-lookup"><span data-stu-id="8b722-164">The POP3 adapter has been tested with and supports receiving messages up to 50 MB in size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b722-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b722-165">See Also</span></span>  
 [<span data-ttu-id="8b722-166">POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="8b722-166">POP3 Adapter</span></span>](../core/pop3-adapter.md)