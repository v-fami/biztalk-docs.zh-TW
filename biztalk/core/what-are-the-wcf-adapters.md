---
title: 何謂 WCF 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18ca8535-3386-4018-8b5b-d32bdb9ebf70
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41c942c7c2ef870b2a61c519e79fb8a124059f03
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="what-are-the-wcf-adapters"></a><span data-ttu-id="d94c7-103">何謂 WCF 配接器？</span><span class="sxs-lookup"><span data-stu-id="d94c7-103">What Are the WCF Adapters?</span></span>
<span data-ttu-id="d94c7-104">Windows Communication Foundation (WCF) 配接器有兩種，一種是接收配接器，另一種是傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="d94c7-104">There are two Windows Communication Foundation (WCF) adapters—a receive adapter and a send adapter.</span></span> <span data-ttu-id="d94c7-105">您可以使用 WCF 接收配接器接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="d94c7-105">You use the WCF receive adapter to receive WCF service requests.</span></span> <span data-ttu-id="d94c7-106">WCF 接收配接器會接收要求、建立 BizTalk 訊息物件，並將關聯的屬性升級為訊息內容。</span><span class="sxs-lookup"><span data-stu-id="d94c7-106">The WCF receive adapter receives a request, creates a BizTalk Message object, and promotes the associated properties to the message context.</span></span> <span data-ttu-id="d94c7-107">您可以使用 WCF 傳送配接器來呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d94c7-107">You use the WCF send adapter to call a WCF service.</span></span> <span data-ttu-id="d94c7-108">WCF 傳送配接器會經由無類型合約來呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d94c7-108">The WCF send adapter calls the WCF services through the typeless contracts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d94c7-109">WCF 配接器不支援使用遠端程序呼叫 (RPC) 樣式的 Web 服務，因為 RPC 樣式之 Web 服務的訊息部分參考的是訊息類型，而不是 WCF 將元素用於訊息部分的訊息元素。</span><span class="sxs-lookup"><span data-stu-id="d94c7-109">The WCF adapters do not support consuming Remote Procedure Call (RPC)-style Web services because the message parts in RPC-style Web services are referring to the message types rather than the message elements where WCF adapters are using elements for the message parts.</span></span> <span data-ttu-id="d94c7-110">建議您透過 [加入 Web 參考] 精靈加入 RPC 樣式的 Web 服務，以便在 BizTalk 專案中使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d94c7-110">We recommend that you add the RPC-style Web services through Add Web Reference wizard for consuming the Web services in BizTalk projects.</span></span>  
  
## <a name="web-services-standards-support"></a><span data-ttu-id="d94c7-111">Web 服務標準支援</span><span class="sxs-lookup"><span data-stu-id="d94c7-111">Web Services Standards Support</span></span>  
 <span data-ttu-id="d94c7-112">WCF 配接器提供諸如 WS-Addressing、WS-Security 和 WS-AtomicTransaction 等 WS-\* 標準的支援。</span><span class="sxs-lookup"><span data-stu-id="d94c7-112">WCF adapters provide the support for WS-\* standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="d94c7-113">此版本的 WCF 配接器不支援 WS-ReliableMessaging。</span><span class="sxs-lookup"><span data-stu-id="d94c7-113">WS-ReliableMessaging is not supported in this release of the WCF adapters.</span></span> <span data-ttu-id="d94c7-114">如需 WCF 支援的規格的清單，請參閱[ http://go.microsoft.com/fwlink/?LinkId=88314 ](http://go.microsoft.com/fwlink/?LinkId=88314)。</span><span class="sxs-lookup"><span data-stu-id="d94c7-114">For a list of specifications supported by WCF, see [http://go.microsoft.com/fwlink/?LinkId=88314](http://go.microsoft.com/fwlink/?LinkId=88314).</span></span>  
  
### <a name="ws-addressing"></a><span data-ttu-id="d94c7-115">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="d94c7-115">WS-Addressing</span></span>  
 <span data-ttu-id="d94c7-116">WCF 配接器需依賴 WCF 所提供的 WS-Addressing 標準支援。</span><span class="sxs-lookup"><span data-stu-id="d94c7-116">WCF adapters rely on the WS-Addressing standard support that is provided by WCF.</span></span> <span data-ttu-id="d94c7-117">WCF 配接器提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="d94c7-117">The following features are available in WCF adapters:</span></span>  
  
-   <span data-ttu-id="d94c7-118">設定在中繼交換要求期間取得的傳送埠端點位址。</span><span class="sxs-lookup"><span data-stu-id="d94c7-118">Configuration of the send port endpoint address obtained during the metadata exchange request.</span></span>  
  
-   <span data-ttu-id="d94c7-119">設定傳送埠端點位址的定位標頭。</span><span class="sxs-lookup"><span data-stu-id="d94c7-119">Configuration of the addressing headers for the send port endpoint address.</span></span>  
  
-   <span data-ttu-id="d94c7-120">設定 BizTalk 接收位置中公開之端點的定位標頭。</span><span class="sxs-lookup"><span data-stu-id="d94c7-120">Configuration of the addressing headers for the endpoint exposed in the BizTalk receive location.</span></span>  
  
### <a name="ws-security"></a><span data-ttu-id="d94c7-121">WS-Security</span><span class="sxs-lookup"><span data-stu-id="d94c7-121">WS-Security</span></span>  
 <span data-ttu-id="d94c7-122">WCF 配接器需依賴 WCF 所提供的安全性標準支援。</span><span class="sxs-lookup"><span data-stu-id="d94c7-122">WCF adapters rely on the security standards support that is provided by WCF.</span></span> <span data-ttu-id="d94c7-123">WCF 配接器支援下列標準：</span><span class="sxs-lookup"><span data-stu-id="d94c7-123">The following standards are supported in WCF adapters:</span></span>  
  
-   <span data-ttu-id="d94c7-124">Web 服務安全性︰ SOAP 訊息安全性 (Ws-security) 1.0 和 1.1 版</span><span class="sxs-lookup"><span data-stu-id="d94c7-124">Web Services Security: SOAP Message Security (WS-Security) 1.0 and 1.1</span></span>  
  
-   <span data-ttu-id="d94c7-125">Web Services Secure Conversation Language (WS-SecureConversation)</span><span class="sxs-lookup"><span data-stu-id="d94c7-125">Web Services Secure Conversation Language (WS-SecureConversation)</span></span>  
  
-   <span data-ttu-id="d94c7-126">Web Services Trust Language (WS-Trust)</span><span class="sxs-lookup"><span data-stu-id="d94c7-126">Web Services Trust Language (WS-Trust)</span></span>  
  
-   <span data-ttu-id="d94c7-127">Web Services Security X.509 Certificate Token Profile</span><span class="sxs-lookup"><span data-stu-id="d94c7-127">Web Services Security X.509 Certificate Token Profile</span></span>  
  
-   <span data-ttu-id="d94c7-128">Web Services Security Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="d94c7-128">Web Services Security Username Token Profile 1.0</span></span>  
  
-   <span data-ttu-id="d94c7-129">Web Services Security Kerberos Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="d94c7-129">Web Services Security Kerberos Token Profile 1.0</span></span>  
  
#### <a name="service-authentication-types"></a><span data-ttu-id="d94c7-130">服務驗證類型</span><span class="sxs-lookup"><span data-stu-id="d94c7-130">Service Authentication Types</span></span>  
 <span data-ttu-id="d94c7-131">支援的 WCF 服務驗證類型如下：</span><span class="sxs-lookup"><span data-stu-id="d94c7-131">The following WCF service authentication types are supported:</span></span>  
  
-   <span data-ttu-id="d94c7-132">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-132">None</span></span>  
  
-   <span data-ttu-id="d94c7-133">視窗</span><span class="sxs-lookup"><span data-stu-id="d94c7-133">Windows</span></span>  
  
-   <span data-ttu-id="d94c7-134">憑證</span><span class="sxs-lookup"><span data-stu-id="d94c7-134">Certificate</span></span>  
  
#### <a name="client-authentication-types"></a><span data-ttu-id="d94c7-135">用戶端驗證類型</span><span class="sxs-lookup"><span data-stu-id="d94c7-135">Client Authentication Types</span></span>  
 <span data-ttu-id="d94c7-136">支援的 WCF 用戶端驗證類型如下：</span><span class="sxs-lookup"><span data-stu-id="d94c7-136">The following WCF client authentication types are supported:</span></span>  
  
-   <span data-ttu-id="d94c7-137">匿名</span><span class="sxs-lookup"><span data-stu-id="d94c7-137">Anonymous</span></span>  
  
-   <span data-ttu-id="d94c7-138">UserName</span><span class="sxs-lookup"><span data-stu-id="d94c7-138">UserName</span></span>  
  
-   <span data-ttu-id="d94c7-139">視窗</span><span class="sxs-lookup"><span data-stu-id="d94c7-139">Windows</span></span>  
  
-   <span data-ttu-id="d94c7-140">憑證</span><span class="sxs-lookup"><span data-stu-id="d94c7-140">Certificate</span></span>  
  
#### <a name="security-modes"></a><span data-ttu-id="d94c7-141">安全性模式</span><span class="sxs-lookup"><span data-stu-id="d94c7-141">Security Modes</span></span>  
 <span data-ttu-id="d94c7-142">支援的安全性模式如下：</span><span class="sxs-lookup"><span data-stu-id="d94c7-142">The following security modes are supported:</span></span>  
  
-   <span data-ttu-id="d94c7-143">傳輸</span><span class="sxs-lookup"><span data-stu-id="d94c7-143">Transport</span></span>  
  
-   <span data-ttu-id="d94c7-144">訊息</span><span class="sxs-lookup"><span data-stu-id="d94c7-144">Message</span></span>  
  
-   <span data-ttu-id="d94c7-145">混合 (傳輸層安全性和訊息層驗證)</span><span class="sxs-lookup"><span data-stu-id="d94c7-145">Mixed (transport-level security and message-level authentication)</span></span>  
  
### <a name="ws-atomictransaction"></a><span data-ttu-id="d94c7-146">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="d94c7-146">WS-AtomicTransaction</span></span>  
 <span data-ttu-id="d94c7-147">WCF-WsHttp、WCF-NetTcp 和 WCF-NetMsmq 配接器支援 WS-AtomicTransaction 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d94c7-147">The WCF-WsHttp, WCF-NetTcp, and WCF-NetMsmq adapters support the WS-AtomicTransaction protocol.</span></span> <span data-ttu-id="d94c7-148">這項支援適用於下列實例：</span><span class="sxs-lookup"><span data-stu-id="d94c7-148">This support allows the following scenarios:</span></span>  
  
-   <span data-ttu-id="d94c7-149">交易式提交訊息至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d94c7-149">Transactional submission of messages to the MessageBox database.</span></span>  
  
-   <span data-ttu-id="d94c7-150">從 MessageBox 至交易式目的地的交易式訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="d94c7-150">Transactional transmission of messages from the MessageBox to a transactional destination.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d94c7-151">交易式範圍受限於 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="d94c7-151">The transactional scope is limited by the MessageBox.</span></span> <span data-ttu-id="d94c7-152">例如，BizTalk 協調流程不能參與用戶端的交易。</span><span class="sxs-lookup"><span data-stu-id="d94c7-152">For example, a BizTalk orchestration cannot participate in a client’s transaction.</span></span> <span data-ttu-id="d94c7-153">同樣地，目的端點也不能參與 BizTalk 協調流程起始的交易。</span><span class="sxs-lookup"><span data-stu-id="d94c7-153">Similarly, a destination endpoint cannot participate in a transaction that is initiated by a BizTalk orchestration.</span></span>  
  
#### <a name="transactional-submission"></a><span data-ttu-id="d94c7-154">交易式提交</span><span class="sxs-lookup"><span data-stu-id="d94c7-154">Transactional Submission</span></span>  
 <span data-ttu-id="d94c7-155">Wcf-wshttp 和 Wcf-nettcp 配接器的交易式提交至 BizTalk Server 會啟用選取 **啟用交易** 接收位置傳輸屬性對話方塊中核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d94c7-155">For the WCF-WsHttp and WCF-NetTcp adapters, transactional submission to BizTalk Server is enabled by selecting the **Enable transactions** check box in the receive location transport properties dialog box.</span></span> <span data-ttu-id="d94c7-156">Wcf-netmsmq 配接器， **交易式** 預設會選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d94c7-156">For the WCF-NetMsmq adapter, the **Transactional** check box is selected by default.</span></span> <span data-ttu-id="d94c7-157">如果訊息提取來源的訊息佇列未標示為交易式，您必須清除這個核取方塊，否則便會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-157">If the message queues from which you are pulling messages are not marked as transactional, you need to clear this check box; otherwise, you will receive an error message.</span></span>  
  
 <span data-ttu-id="d94c7-158">如果交易功能已啟用，訊息便會利用戶端的交易提交到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d94c7-158">If the transaction functionality is enabled, messages are submitted to the MessageBox database by using clients’ transactions.</span></span> <span data-ttu-id="d94c7-159">如果用戶端嘗試在交易式範圍之外提交訊息，配接器會將例外狀況傳回到用戶端，</span><span class="sxs-lookup"><span data-stu-id="d94c7-159">If a client attempts to submit the messages outside the transactional scope, the adapter will return an exception back to the client.</span></span> <span data-ttu-id="d94c7-160">但是不會擱置任何訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-160">However, no messages will be suspended.</span></span> <span data-ttu-id="d94c7-161">如果交易功能已停用，訊息將提交到 MessageBox 資料庫，而且不會使用用戶端的交易。</span><span class="sxs-lookup"><span data-stu-id="d94c7-161">If the transaction functionality is disabled, messages are submitted to the MessageBox without using clients’ transactions.</span></span> <span data-ttu-id="d94c7-162">如果用戶端嘗試在交易式範圍內提交訊息，配接器會將例外狀況傳回到用戶端，而且不會擱置任何訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-162">If a client attempts to submit messages inside the transactional scope, the adapter will return an exception back to the client, and no messages will be suspended.</span></span>  
  
#### <a name="transactions-and-receive-location-type"></a><span data-ttu-id="d94c7-163">交易和接收位置類型</span><span class="sxs-lookup"><span data-stu-id="d94c7-163">Transactions and Receive Location Type</span></span>  
 <span data-ttu-id="d94c7-164">交易式提交只適用於單向接收位置。</span><span class="sxs-lookup"><span data-stu-id="d94c7-164">Transactional submission is available only for one-way receive locations.</span></span> <span data-ttu-id="d94c7-165">如果用戶端嘗試在雙向接收位置的交易式範圍中提交訊息，系統會將例外狀況傳回到用戶端，而且不會擱置任何訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-165">If a client attempts to submit messages in a transactional scope for a two-way receive location, an exception will be returned back to the client, and no messages will be suspended.</span></span>  
  
#### <a name="transactional-transmission"></a><span data-ttu-id="d94c7-166">交易式傳輸</span><span class="sxs-lookup"><span data-stu-id="d94c7-166">Transactional Transmission</span></span>  
 <span data-ttu-id="d94c7-167">Wcf-wshttp 和 Wcf-nettcp 配接器，BizTalk Server 從交易式傳輸會啟用選取 **啟用交易** 傳送埠傳輸屬性對話方塊中核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d94c7-167">For the WCF-WsHttp and WCF-NetTcp adapters, transactional transmission from BizTalk Server is enabled by selecting the **Enable transactions** check box in the send port transport properties dialog box.</span></span> <span data-ttu-id="d94c7-168">Wcf-netmsmq 配接器， **交易式** 預設會選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d94c7-168">For the WCF-NetMsmq adapter, the **Transactional** check box is selected by default.</span></span> <span data-ttu-id="d94c7-169">如果訊息傳送目標的訊息佇列未標示為交易式，您必須清除這個核取方塊，否則便會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-169">If the message queues to which you are sending messages are not marked as transactional, you need to clear this check box; otherwise, you will receive an error message.</span></span>  
  
 <span data-ttu-id="d94c7-170">如果交易功能已啟用，訊息便會從正在進行交易的 MessageBox 資料庫中傳輸並刪除。</span><span class="sxs-lookup"><span data-stu-id="d94c7-170">If the transaction functionality is enabled, messages are transmitted and deleted from the MessageBox database under transaction.</span></span> <span data-ttu-id="d94c7-171">如果目的地服務在接收訊息之後執行過任何工作，而且沒有從 MessageBox 刪除訊息，則交易將會中止，而且服務的所有交易工作也都會回復。</span><span class="sxs-lookup"><span data-stu-id="d94c7-171">If the destination service has performed any work after receiving the message, and the message is not deleted from the MessageBox, then the transaction will be aborted and all transaction work on the service will be rolled back.</span></span> <span data-ttu-id="d94c7-172">如果交易功能已停用，則會以不使用交易的方式，從正在進行交易的 MessageBox 資料庫傳輸並刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="d94c7-172">If the transaction functionality is disabled, messages are transmitted and deleted from the MessageBox without using transactions.</span></span>  
  
## <a name="single-sign-on-support"></a><span data-ttu-id="d94c7-173">單一登入支援</span><span class="sxs-lookup"><span data-stu-id="d94c7-173">Single Sign-On Support</span></span>  
 <span data-ttu-id="d94c7-174">您可以模擬及取得企業單一登入 (SSO) 票證，以便將 SSO 與 WCF 配接器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d94c7-174">You can impersonate and acquire the Enterprise Single Sign-On (SSO) ticket for using SSO with WCF adapters.</span></span> <span data-ttu-id="d94c7-175">如需如何搭配 WCF 配接器使用 SSO 的詳細資訊，請參閱[WCF 配接器的單一登入支援](../core/single-sign-on-support-for-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="d94c7-175">For more information about how to use SSO with WCF adapters, see [Single Sign-On Support for the WCF Adapters](../core/single-sign-on-support-for-the-wcf-adapters.md).</span></span>  
  
 <span data-ttu-id="d94c7-176">下表摘要說明將 SSO 支援與 WCF 接收配接器搭配使用時無法支援的實例。</span><span class="sxs-lookup"><span data-stu-id="d94c7-176">The following table summarizes the scenarios that are not supported when using SSO support with the WCF receive adapters.</span></span>  
  
|<span data-ttu-id="d94c7-177">安全性模式</span><span class="sxs-lookup"><span data-stu-id="d94c7-177">Security mode</span></span>|<span data-ttu-id="d94c7-178">認證</span><span class="sxs-lookup"><span data-stu-id="d94c7-178">Credential</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="d94c7-179">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-179">None</span></span>|<span data-ttu-id="d94c7-180">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-180">None</span></span>|  
|<span data-ttu-id="d94c7-181">傳輸</span><span class="sxs-lookup"><span data-stu-id="d94c7-181">Transport</span></span>|<span data-ttu-id="d94c7-182">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-182">None</span></span>|  
|<span data-ttu-id="d94c7-183">訊息</span><span class="sxs-lookup"><span data-stu-id="d94c7-183">Message</span></span>|<span data-ttu-id="d94c7-184">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-184">None</span></span>|  
|<span data-ttu-id="d94c7-185">TransportWithMessageCredentials</span><span class="sxs-lookup"><span data-stu-id="d94c7-185">TransportWithMessageCredentials</span></span>|<span data-ttu-id="d94c7-186">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-186">None</span></span>|  
|<span data-ttu-id="d94c7-187">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="d94c7-187">TransportCredentialOnly</span></span>|<span data-ttu-id="d94c7-188">無</span><span class="sxs-lookup"><span data-stu-id="d94c7-188">None</span></span>|  
  
## <a name="wcf-extensibility"></a><span data-ttu-id="d94c7-189">WCF 擴充性</span><span class="sxs-lookup"><span data-stu-id="d94c7-189">WCF Extensibility</span></span>  
 <span data-ttu-id="d94c7-190">您可以透過開發下列延伸模組並將這些模組用於 WCF-Custom 和 WCF-CustomIsolated 配接器的方式，來擴充 WCF 的功能：</span><span class="sxs-lookup"><span data-stu-id="d94c7-190">You can extend the functionality of WCF by developing the following extensions and using them with the WCF-Custom and WCF-CustomIsolated adapters:</span></span>  
  
-   <span data-ttu-id="d94c7-191">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d94c7-191">Custom bindings</span></span>  
  
-   <span data-ttu-id="d94c7-192">自訂繫結元素</span><span class="sxs-lookup"><span data-stu-id="d94c7-192">Custom binding elements</span></span>  
  
### <a name="custom-bindings"></a><span data-ttu-id="d94c7-193">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d94c7-193">Custom Bindings</span></span>  
 <span data-ttu-id="d94c7-194">自訂繫結的開發方式是將個別繫結元素封裝成容器，以公開特定使用實例的組態屬性子集。</span><span class="sxs-lookup"><span data-stu-id="d94c7-194">Custom bindings are developed by packaging individual binding elements into a container that exposes a subset of the configuration properties for a particular usage scenario.</span></span> <span data-ttu-id="d94c7-195">您必須將組件安裝到全域組件快取 (GAC)，然後再將延伸模組元素加入電腦組態檔中，以註冊繫結延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d94c7-195">You need to register the binding extension by installing the assembly into the global assembly cache (GAC) and then adding the extension element to the machine configuration file.</span></span> <span data-ttu-id="d94c7-196">若要使用自訂繫結，您必須在 BizTalk 群組的每一部伺服器上設定繫結。</span><span class="sxs-lookup"><span data-stu-id="d94c7-196">To use the custom bindings, you need to set up the binding on every server in the BizTalk group.</span></span> <span data-ttu-id="d94c7-197">在安裝繫結之後，它就會變成 WCF-Custom 和 WCF-CustomIsolated 配接器的可見項目。</span><span class="sxs-lookup"><span data-stu-id="d94c7-197">After the binding is installed, it will be visible to the WCF-Custom and WCF-CustomIsolated adapters.</span></span> <span data-ttu-id="d94c7-198">WCF-Custom 和 WCF-CustomIsolated 配接器將會在繫結組態項目上使用反映，以取得繫結組態屬性。</span><span class="sxs-lookup"><span data-stu-id="d94c7-198">The WCF-Custom and WCF-CustomIsolated adapters will get the binding configuration properties by using reflection on the binding configuration elements.</span></span>  
  
### <a name="custom-binding-elements"></a><span data-ttu-id="d94c7-199">自訂繫結元素</span><span class="sxs-lookup"><span data-stu-id="d94c7-199">Custom Binding Elements</span></span>  
 <span data-ttu-id="d94c7-200">開發自訂繫結元素的方式是加入或修改特定的傳輸通道元件。</span><span class="sxs-lookup"><span data-stu-id="d94c7-200">Custom binding elements are developed by adding or modifying certain transport channel components.</span></span> <span data-ttu-id="d94c7-201">例如，自訂解壓縮元件會封裝成繫結元素，或者 UDP 傳輸會表示為繫結元素。</span><span class="sxs-lookup"><span data-stu-id="d94c7-201">For example, a custom decompression component is packaged as a binding element, or a UDP transport is represented as a binding element.</span></span> <span data-ttu-id="d94c7-202">這些繫結元素可以在 WCF 配接器內使用。</span><span class="sxs-lookup"><span data-stu-id="d94c7-202">These binding elements can be used inside the WCF adapters.</span></span> <span data-ttu-id="d94c7-203">您可以定義通道堆疊，使其將自訂繫結元素與其他現成或自訂的繫結元素搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d94c7-203">You can define a channel stack that uses the custom binding element in combination with other out-of-box or custom binding elements.</span></span> <span data-ttu-id="d94c7-204">您必須將組件安裝到 GAC，然後再將延伸模組元素加入電腦組態檔中，以註冊繫結元件延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d94c7-204">You need to register the binding element extension by installing the assembly into the GAC and then adding the extension element to the machine configuration file.</span></span> <span data-ttu-id="d94c7-205">若要使用自訂繫結，您必須在 BizTalk 群組的每一部伺服器上設定繫結。</span><span class="sxs-lookup"><span data-stu-id="d94c7-205">To use the custom bindings, you need to set up the binding on every server in the BizTalk group.</span></span> <span data-ttu-id="d94c7-206">若要使用自訂繫結項目，您可以選取 **CustomBinding** 繫結類型，然後新增、 修改或重新排列的繫結項目所需的順序。</span><span class="sxs-lookup"><span data-stu-id="d94c7-206">To use the custom binding elements, you can select the **CustomBinding** binding type and then add, modify, or rearrange the binding elements in a desired order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d94c7-207">本節內容</span><span class="sxs-lookup"><span data-stu-id="d94c7-207">In This Section</span></span>  
  
-   [<span data-ttu-id="d94c7-208">WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="d94c7-208">WCF Receive Adapter</span></span>](../core/wcf-receive-adapter.md)  
  
-   [<span data-ttu-id="d94c7-209">WCF 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="d94c7-209">WCF Send Adapter</span></span>](../core/wcf-send-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="d94c7-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d94c7-210">See Also</span></span>  
-  [<span data-ttu-id="d94c7-211">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="d94c7-211">WCF Adapters</span></span>](../core/wcf-adapters.md)   
-  <span data-ttu-id="d94c7-212">**WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d94c7-212">**WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>