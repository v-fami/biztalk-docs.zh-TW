---
title: HTTP 傳送配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e69308b4-421f-4d7c-b9bb-ee086df03272
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2ddd2a3fa4b8bb2f97e25809121fa11b1f473f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999639"
---
# <a name="http-send-adapter"></a><span data-ttu-id="adabd-102">HTTP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="adabd-102">HTTP Send Adapter</span></span>
<span data-ttu-id="adabd-103">HTTP 傳送配接器會從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取得訊息，並在 HTTP POST 要求時，將它們傳送到目的地 URL。</span><span class="sxs-lookup"><span data-stu-id="adabd-103">The HTTP send adapter gets messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and sends them to a destination URL on an HTTP POST request.</span></span> <span data-ttu-id="adabd-104">HTTP 傳送配接器會從 BizTalk 訊息物件的內文部分取得訊息內容。</span><span class="sxs-lookup"><span data-stu-id="adabd-104">The HTTP send adapter gets the message content from the body part of the BizTalk Message object.</span></span> <span data-ttu-id="adabd-105">HTTP 傳送配接器會忽略 BizTalk 訊息物件中的所有其他部分。</span><span class="sxs-lookup"><span data-stu-id="adabd-105">The HTTP send adapter ignores all other parts of the BizTalk Message object.</span></span>  
  
 <span data-ttu-id="adabd-106">在配接器傳送訊息到目的地 URL 且「BizTalk 傳訊引擎」收到 HTTP 成功狀態碼之後，HTTP 傳送配接器會從 MessageBox 資料庫刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="adabd-106">After the adapter sends the message to a destination URL and the BizTalk Messaging Engine receives the HTTP success status code, the HTTP send adapter deletes the message from the MessageBox database.</span></span>  
  
 <span data-ttu-id="adabd-107">在傳送埠上支援並可設定 HTTP 訊息的重新導向。</span><span class="sxs-lookup"><span data-stu-id="adabd-107">Redirection of HTTP messages is supported and can be configured on the send port.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="adabd-108"> 裝載 HTTP 傳送配接器做為原生 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="adabd-108"> hosts the HTTP send adapter as a native BizTalk application.</span></span> <span data-ttu-id="adabd-109">它支援單向傳送訊息以及請求-回應傳輸。</span><span class="sxs-lookup"><span data-stu-id="adabd-109">It supports one-way sending of messages as well a solicit-response transmission.</span></span> <span data-ttu-id="adabd-110">HTTP 傳送配接器的傳送位置是透過傳送埠所設定的不同 URL。</span><span class="sxs-lookup"><span data-stu-id="adabd-110">The send location for the HTTP send adapter is a distinct URL that you configure through the send port.</span></span> <span data-ttu-id="adabd-111">此唯一 URL 可包含附加到基底 URL 的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="adabd-111">This unique URL can include query strings appended to the base URL.</span></span>  
  
## <a name="batching-support-for-the-http-send-adapter"></a><span data-ttu-id="adabd-112">HTTP 傳送配接器的批次支援</span><span class="sxs-lookup"><span data-stu-id="adabd-112">Batching Support for the HTTP Send Adapter</span></span>  
 <span data-ttu-id="adabd-113">HTTP 傳送配接器不支援批次作業。</span><span class="sxs-lookup"><span data-stu-id="adabd-113">The HTTP send adapter does not support batching operations.</span></span>  
  
## <a name="chunked-encoding-support-for-the-http-send-adapter"></a><span data-ttu-id="adabd-114">HTTP 傳送配接器的區塊編碼支援</span><span class="sxs-lookup"><span data-stu-id="adabd-114">Chunked Encoding Support for the HTTP Send Adapter</span></span>  
 <span data-ttu-id="adabd-115">如果**啟用區塊編碼**啟用組態選項，則 HTTP 傳送配接器會傳送使用區塊編碼，如果要求的大小超過 8 KB 的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="adabd-115">If the **Enable chunked encoding** configuration option is enabled, then the HTTP send adapter sends request messages using chunked encoding if the request size exceeds 8 KB.</span></span> <span data-ttu-id="adabd-116">若已使用 HTTP Proxy 伺服器，則 HTTP 傳送配接器不會使用區塊編碼，並且永遠會在傳送之前處理資料。</span><span class="sxs-lookup"><span data-stu-id="adabd-116">If the HTTP proxy server is used, the HTTP send adapter does not use chunked encoding and always stages the data before sending.</span></span> <span data-ttu-id="adabd-117">**啟用區塊編碼**預設會啟用組態選項。</span><span class="sxs-lookup"><span data-stu-id="adabd-117">The **Enable chunked encoding** configuration option is enabled by default.</span></span>  
  
 <span data-ttu-id="adabd-118">傳送配接器收到回應訊息時，可以接受有區塊編碼內文部分的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="adabd-118">When the send adapter receives a response message, it can accept response messages with a chunked encoded body part.</span></span>  
  
## <a name="client-authentication-for-the-http-send-adapter"></a><span data-ttu-id="adabd-119">HTTP 傳送配接器的用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="adabd-119">Client Authentication for the HTTP Send Adapter</span></span>  
 <span data-ttu-id="adabd-120">HTTP 傳送配接器會使用下列其中一種驗證類型在目的地伺服器進行驗證：</span><span class="sxs-lookup"><span data-stu-id="adabd-120">The HTTP send adapter authenticates with the destination server by using one of the following authentication types:</span></span>  
  
- <span data-ttu-id="adabd-121">**匿名的。**</span><span class="sxs-lookup"><span data-stu-id="adabd-121">**Anonymous.**</span></span> <span data-ttu-id="adabd-122">HTTP 配接器在連接到目的地伺服器時，不會傳送任何認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-122">The HTTP adapter does not send any credentials when connecting to the destination server.</span></span> <span data-ttu-id="adabd-123">若目的地伺服器允許匿名驗證，則會使用在目的地伺服器上已設定之匿名帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-123">If the destination server permits anonymous authentication then the credentials of the configured anonymous account on the destination server are used.</span></span>  
  
- <span data-ttu-id="adabd-124">**基本的。**</span><span class="sxs-lookup"><span data-stu-id="adabd-124">**Basic.**</span></span> <span data-ttu-id="adabd-125">HTTP 配接器透過 HTTP 連線以純文字傳送使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="adabd-125">The HTTP adapter sends the user name and password over an HTTP connection in plain text.</span></span>  
  
- <span data-ttu-id="adabd-126">**摘要。**</span><span class="sxs-lookup"><span data-stu-id="adabd-126">**Digest.**</span></span> <span data-ttu-id="adabd-127">HTTP 配接器透過 HTTP 連線以加密格式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="adabd-127">The HTTP adapter sends passwords in an encrypted format over the HTTP connection.</span></span>  
  
- <span data-ttu-id="adabd-128">**Kerberos。**</span><span class="sxs-lookup"><span data-stu-id="adabd-128">**Kerberos.**</span></span> <span data-ttu-id="adabd-129">不會透過 HTTP 連線傳送使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="adabd-129">Neither the user name nor the password is sent over an HTTP connection.</span></span> <span data-ttu-id="adabd-130">HTTP 配接器會使用 HTTP 傳送配接器在此程序之下執行此驗證類型的程序之認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-130">The HTTP adapter uses the credentials of the process under which the HTTP send adapter runs for this authentication type.</span></span>  
  
  <span data-ttu-id="adabd-131">此外，HTTP 傳送配接器還可以在伺服器要求或接受用戶端「安全通訊端層」(SSL) 憑證時，提供此憑證給 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="adabd-131">Additionally, the HTTP send adapter can provide a client Secure Sockets Layer (SSL) certificate to the Web server if the server requires or accepts it.</span></span>  
  
## <a name="client-certificates-for-the-http-send-adapter"></a><span data-ttu-id="adabd-132">HTTP 傳送配接器的用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="adabd-132">Client Certificates for the HTTP Send Adapter</span></span>  
 <span data-ttu-id="adabd-133">HTTP 傳送配接器可以與接受或要求用戶端憑證之伺服器建立安全連線。</span><span class="sxs-lookup"><span data-stu-id="adabd-133">The HTTP send adapter can establish a secure connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="adabd-134">若已指定用戶端憑證，則 HTTP 傳送配接器在與要求或接受用戶端憑證的伺服器連線時會使用憑證。</span><span class="sxs-lookup"><span data-stu-id="adabd-134">If a client certificate is specified, the HTTP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="adabd-135">若未指定用戶端憑證，但目的地伺服器要求用戶端憑證，則 HTTP 傳送配接器無法傳送訊息並依照標準重試邏輯處理。</span><span class="sxs-lookup"><span data-stu-id="adabd-135">If the client certificate is not specified and the destination server requires client certificates, the HTTP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="adabd-136">HTTP 傳送配接器會使用執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序的帳戶之個人存放區中的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="adabd-136">The HTTP send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="adabd-137">憑證是由其指紋指定。</span><span class="sxs-lookup"><span data-stu-id="adabd-137">The certificate is specified by its thumbprint.</span></span> <span data-ttu-id="adabd-138">若 HTTP 傳送配接器因故無法載入憑證，則會擱置所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="adabd-138">If the HTTP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
## <a name="single-sign-on-support-for-the-http-adapter"></a><span data-ttu-id="adabd-139">HTTP 配接器的單一登入支援</span><span class="sxs-lookup"><span data-stu-id="adabd-139">Single Sign-On Support for the HTTP Adapter</span></span>  
 <span data-ttu-id="adabd-140">您可以使用 [BizTalk 管理] 主控台來設定「企業單一登入」(SSO)，以便與 HTTP 接收位置或傳送埠搭配使用。</span><span class="sxs-lookup"><span data-stu-id="adabd-140">You can configure Enterprise Single Sign-On (SSO) for use with the HTTP receive location or send port by using BizTalk Administration console.</span></span> <span data-ttu-id="adabd-141">本主題描述 SSO 如何與 HTTP 配接器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="adabd-141">This topic describes how SSO works with the HTTP adapter.</span></span>  
  
 <span data-ttu-id="adabd-142">**單一登入 」 支援之 http 接收位置**</span><span class="sxs-lookup"><span data-stu-id="adabd-142">**Single Sign-On Support for the HTTP Receive Location**</span></span>  
  
 <span data-ttu-id="adabd-143">當 Microsoft Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="adabd-143">When an HTTP request is received by Microsoft Internet Information Services (IIS) from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="adabd-144">Internet Server Application Programming Interface (ISAPI) 延伸模組會模擬 Microsoft Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="adabd-144">The Internet Server Application Programming Interface (ISAPI) extension impersonates the Microsoft Windows user and then calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="adabd-145">此票證會儲存為**SSOTicket**訊息的內容中的屬性。</span><span class="sxs-lookup"><span data-stu-id="adabd-145">This ticket is stored as the **SSOTicket** property in the context of the message.</span></span>  
  
 <span data-ttu-id="adabd-146">在通過實例中，「BizTalk 傳訊引擎」會將訊息導向至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="adabd-146">In the pass-through scenario, the BizTalk Messaging Engine directs the message to the MessageBox database.</span></span> <span data-ttu-id="adabd-147">當配接器從 MessageBox 資料庫收到訊息時，HTTP 配接器會呼叫**ISSOTicket.RedeemTicket 方法**具有加密票證及應用程式名稱，以擷取從後端認證SSO 存放區。</span><span class="sxs-lookup"><span data-stu-id="adabd-147">When the adapter receives the message from the MessageBox database, the HTTP adapter calls the **ISSOTicket.RedeemTicket Method** with the encrypted ticket along with the application name to retrieve the back-end credentials from the SSO store.</span></span> <span data-ttu-id="adabd-148">HTTP 配接器接著就會使用外部認證連接到後端系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="adabd-148">The HTTP adapter then uses the external credentials to connect to the back-end system and process the request.</span></span> <span data-ttu-id="adabd-149">如需分支機構應用程式的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="adabd-149">For more information about the affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
 <span data-ttu-id="adabd-150">在協調流程叫用配接器的實例中，「BizTalk 傳訊引擎」會傳送此訊息至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="adabd-150">In the scenario where an orchestration invokes the adapter, the BizTalk Messaging Engine sends this message to the MessageBox database.</span></span> <span data-ttu-id="adabd-151">協調流程應確保同時**SSOTicket**內容屬性和**Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID**包含票證的訊息內容屬性維護。</span><span class="sxs-lookup"><span data-stu-id="adabd-151">The orchestration should ensure that both the **SSOTicket** context property and the **Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID** context property of the message that contains the ticket are maintained.</span></span> <span data-ttu-id="adabd-152">當配接器從 MessageBox 資料庫收到這個訊息時，配接器會呼叫**RedeemTicket**具有加密票證從 SSO 存放區擷取後端認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-152">When the adapter receives this message from the MessageBox database, the adapter calls **RedeemTicket** with the encrypted ticket to retrieve the back-end credentials from the SSO store.</span></span> <span data-ttu-id="adabd-153">設計排程的使用者應該特別將此屬性複製到訊息中。</span><span class="sxs-lookup"><span data-stu-id="adabd-153">The user designing the schedule should specifically copy this property to the message.</span></span>  
  
 <span data-ttu-id="adabd-154">**HTTP 傳送配接器的單一登入支援**</span><span class="sxs-lookup"><span data-stu-id="adabd-154">**Single Sign-On Support for the HTTP Send Adapters**</span></span>  
  
 <span data-ttu-id="adabd-155">如果已啟用 SSO，當 HTTP 傳送埠收到的訊息**Secure**屬性，它會呼叫 SSO 伺服器以驗證並贖回分支機構應用程式的票證。</span><span class="sxs-lookup"><span data-stu-id="adabd-155">If SSO is enabled, when an HTTP send port receives a message with the **Secure** property, it calls the SSO server to validate and redeem the ticket for an affiliate application.</span></span> <span data-ttu-id="adabd-156">分支機構應用程式的管理應用程式、分支機構系統管理員或 SSO 系統管理員可以呼叫 SSO 贖回票證。</span><span class="sxs-lookup"><span data-stu-id="adabd-156">The administration application, affiliate administrators, or SSO administrators for the affiliate application can call SSO to redeem a ticket.</span></span> <span data-ttu-id="adabd-157">接著 SSO 會解密票證並取得後端認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-157">SSO then decrypts the ticket and obtains the back-end credentials.</span></span> <span data-ttu-id="adabd-158">通過和協調流程實例與 HTTP 傳送埠相同。</span><span class="sxs-lookup"><span data-stu-id="adabd-158">The pass-through and orchestration scenario are the same as for the HTTP send port.</span></span>  
  
 <span data-ttu-id="adabd-159">依照預設，會停用 HTTP 傳送埠的 SSO。</span><span class="sxs-lookup"><span data-stu-id="adabd-159">By default, SSO is disabled for the HTTP send port.</span></span> <span data-ttu-id="adabd-160">如需啟用 SSO 的 HTTP 傳送埠的詳細資訊，請參閱[設定 HTTP 傳送埠](../core/configuring-an-http-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="adabd-160">For more information about enabling SSO for the HTTP send port, see [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adabd-161">您只能使用單一登入使用基本和摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="adabd-161">You can only use Single Sign-On with basic and digest authentication.</span></span>  
  
 <span data-ttu-id="adabd-162">若要正確地實作 HTTP 接收配接器和傳送配接器的「單一登入」支援，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="adabd-162">To correctly implement Single Sign On support for the HTTP receive and send adapter the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="adabd-163">必須在下列各處指定相同的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="adabd-163">The same user account must be specified in the following places:</span></span>  
  
    -   <span data-ttu-id="adabd-164">IIS 虛擬目錄 (由 HTTP 接收配接器所監控) 之應用程式集區識別 (IIS 7.0) 或裝載 COM+ 應用程式識別。</span><span class="sxs-lookup"><span data-stu-id="adabd-164">The application pool identity (IIS 7.0) or hosting COM+ application identity for the IIS virtual directory that is monitored by the HTTP receive adapter.</span></span> <span data-ttu-id="adabd-165">如需有關設定 IIS 的 HTTP 接收位置，請參閱[針對 HTTP 接收位置設定 IIS 如何](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="adabd-165">For more information about configuring IIS for HTTP receive locations, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
    -   <span data-ttu-id="adabd-166">在中執行 HTTP 配接器的外掛式主控件執行個體所使用的登入認證。</span><span class="sxs-lookup"><span data-stu-id="adabd-166">The logon credentials used for the isolated host instance that the HTTP adapter is running in.</span></span> <span data-ttu-id="adabd-167">如需如何設定主控件執行個體的登入認證的詳細資訊，請參閱[如何修改主控件執行個體內容](../core/how-to-modify-host-instance-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="adabd-167">For information about how to configure the logon credentials for a host instance, see [How to Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md).</span></span>  
  
-   <span data-ttu-id="adabd-168">HTTP 配接器使用的外掛式主控件必須設定為 [信任的驗證]。</span><span class="sxs-lookup"><span data-stu-id="adabd-168">The isolated host that the HTTP adapter is using must be configured as Authentication Trusted.</span></span> <span data-ttu-id="adabd-169">如需如何將主控件設定為信任的驗證資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="adabd-169">For information about how to configure a host as Authentication Trusted, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="negative-acknowledgment-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapter"></a><span data-ttu-id="adabd-170">由 HTTP 或 SOAP 配接器為失敗傳輸產生的負值通知 (NACK) 訊息</span><span class="sxs-lookup"><span data-stu-id="adabd-170">Negative Acknowledgment (NACK) Messages Generated for Failed Transmissions by the HTTP or SOAP Adapter</span></span>  
 <span data-ttu-id="adabd-171">當訊息已成功傳輸時，若已啟用 [傳遞通知]，則「BizTalk 傳訊引擎」會將相關的通知 (ACK) 訊息發佈到 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="adabd-171">When a message is successfully transmitted, the BizTalk Messaging Engine publishes an associated acknowledgment (ACK) message to the MessageBox if delivery notifications are enabled.</span></span> <span data-ttu-id="adabd-172">同樣的，當「BizTalk 傳訊引擎」擱置訊息或是協調流程引擎擱置協調流程時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將相關的負值通知 (NACK) 訊息發佈到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="adabd-172">Likewise, when a message is suspended by the BizTalk Messaging Engine or an orchestration is suspended by the orchestration engine, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publishes an associated negative acknowledgment (NACK) message to the MessageBox.</span></span> <span data-ttu-id="adabd-173">NACK 訊息包含內容屬性以及由一個 SOAP 錯誤組成的訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="adabd-173">The NACK message contains context properties and a message body part that consists of a SOAP fault.</span></span> <span data-ttu-id="adabd-174">若 NACK 訊息是由於 HTTP 或 SOAP 配接器傳輸失敗而產生，則 SOAP 錯誤會包含來自目的地 Web 伺服器回應的標頭項目與內文項目。</span><span class="sxs-lookup"><span data-stu-id="adabd-174">If the NACK message is generated due to a failed transmission from the HTTP or SOAP adapter, the SOAP fault contains the Headers element and the Body element of the response from the destination Web server.</span></span> <span data-ttu-id="adabd-175">下列範例是由於 HTTP 傳輸失敗而產生的 NACK 中的 SOAP 錯誤：</span><span class="sxs-lookup"><span data-stu-id="adabd-175">The following is an example of the SOAP fault in a NACK generated for a failed HTTP transmission:</span></span>  
  
```  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
   <SOAP:Body>  
      <SOAP:Fault>  
         <faultcode>Microsoft BizTalk Server Negative Acknowledgment</faultcode>   
         <faultstring>An error occurred while processing the message, refer to the details section for more information</faultstring>   
         <faultactor>http://localhost/receivestandard.asp</faultactor>   
         <detail>  
            <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
            <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
            <ErrorCode>0x80131600</ErrorCode>  
            <ErrorCategory>0</ErrorCategory>  
            <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
            <ErrorDetail>  
            <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
               <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
               <Body>We could not locate the page you requested. Please check the URL.</Body>  
            </HttpErrorDetail>  
            </ErrorDetail>  
            </ns0:NACK>  
         </detail>  
      </SOAP:Fault>  
   </SOAP:Body>  
</SOAP:Envelope>  
```  
  
> [!NOTE]
>  <span data-ttu-id="adabd-176">標頭項目和內文項目限制為 48 KB。</span><span class="sxs-lookup"><span data-stu-id="adabd-176">The Headers element and the Body element are limited to 48 KB.</span></span> <span data-ttu-id="adabd-177">標頭項目會四捨五入為最接近但不超過限制的完整標頭值組。</span><span class="sxs-lookup"><span data-stu-id="adabd-177">The Headers element is rounded to the nearest complete header value pair without exceeding the limit.</span></span> <span data-ttu-id="adabd-178">內文項目會截斷為 48 KB。</span><span class="sxs-lookup"><span data-stu-id="adabd-178">The Body element is truncated to 48 KB.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adabd-179">若 NACK 與 ACK 訊息沒有相符的訂閱，則會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="adabd-179">NACK and ACK messages are discarded if there are no matching subscriptions for them.</span></span> <span data-ttu-id="adabd-180">「BizTalk 傳訊引擎」會擱置 NACK 與 ACK 訊息。</span><span class="sxs-lookup"><span data-stu-id="adabd-180">NACK and ACK messages are not suspended by the BizTalk Messaging Engine.</span></span>  
  
 <span data-ttu-id="adabd-181">若要訂閱 NACK 訊息，可以執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="adabd-181">To subscribe to a NACK message, you can do one of the following:</span></span>  
  
- <span data-ttu-id="adabd-182">使用適當訊息內容屬性的篩選建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="adabd-182">Create a send port with a filter for the appropriate message context property.</span></span> <span data-ttu-id="adabd-183">請參閱**訊息內容屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需系統訊息內容屬性的清單包括相關訊息通知。</span><span class="sxs-lookup"><span data-stu-id="adabd-183">See **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for a listing of system message context properties including those related to message acknowledgment.</span></span>  
  
- <span data-ttu-id="adabd-184">從標記為協調流程連接埠傳送**Delivery Notification = Transmitted**。</span><span class="sxs-lookup"><span data-stu-id="adabd-184">Send from an orchestration port marked with **Delivery Notification = Transmitted**.</span></span> <span data-ttu-id="adabd-185">如果協調流程連接埠會標示**Delivery Notification = Transmitted**，協調流程會等候，直到它收到 ACK 或 NACK 訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="adabd-185">If an orchestration port is marked with **Delivery Notification = Transmitted**, the orchestration will wait until it receives either an ACK or a NACK for the message that was transmitted.</span></span> <span data-ttu-id="adabd-186">若產生的是 NACK，則會傳送到協調流程，且協調流程會擲回 DeliveryFailureException。</span><span class="sxs-lookup"><span data-stu-id="adabd-186">If a NACK is generated then it will be routed to the orchestration and the orchestration will throw a DeliveryFailureException.</span></span> <span data-ttu-id="adabd-187">DeliveryFailureException 會從 NACK 訊息內文內包含的 SOAP 錯誤還原序列化。</span><span class="sxs-lookup"><span data-stu-id="adabd-187">The DeliveryFailureException is deserialized from the SOAP fault that is contained within the NACK message body.</span></span> <span data-ttu-id="adabd-188">若要從傳回協調流程的 SOAP 錯誤中擷取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，接著從 SOAP Detail 區段存取 InnerXml。</span><span class="sxs-lookup"><span data-stu-id="adabd-188">To retrieve the exception message string from the SOAP fault that is returned to the orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml from the SOAP Detail section.</span></span> <span data-ttu-id="adabd-189">下列程式碼範例示範如何執行此操作：</span><span class="sxs-lookup"><span data-stu-id="adabd-189">The following code sample demonstrates how to do this:</span></span>  
  
  ```  
  // Cast the DeliveryFailureException to a SoapException…  
  System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
  System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
  //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
  //object type created in an Exception handler  
  
  ```  
  
   <span data-ttu-id="adabd-190">上述程式碼範例傳回的 XML 片段應和下列類似：</span><span class="sxs-lookup"><span data-stu-id="adabd-190">The code sample above will return an XML fragment similar to the following:</span></span>  
  
  ```  
  <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
  <ErrorCode>0x80131600</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
  <ErrorDetail>  
  <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
     <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
     <Body>We could not locate the page you requested. Please check the URL.</Body>  
  </HttpErrorDetail>  
  </ErrorDetail>  
  </ns0:NACK>  
  ```  
  
## <a name="see-also"></a><span data-ttu-id="adabd-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adabd-191">See Also</span></span>  
 [<span data-ttu-id="adabd-192">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="adabd-192">HTTP Adapter</span></span>](../core/http-adapter.md)  
<span data-ttu-id="adabd-193">**SSO COM 物件** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="adabd-193">**SSO COM objects** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>