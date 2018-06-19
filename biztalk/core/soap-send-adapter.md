---
title: SOAP 傳送配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d65218d-516b-4e45-a824-272ef6ef298c
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f59babb164458f7a5d072809d038fb253482553d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278854"
---
# <a name="soap-send-adapter"></a><span data-ttu-id="1b7fc-102">SOAP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="1b7fc-102">SOAP Send Adapter</span></span>
<span data-ttu-id="1b7fc-103">您可以使用 SOAP 傳送配接器來呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-103">You use the SOAP send adapter to call a Web service.</span></span> <span data-ttu-id="1b7fc-104">SOAP 傳送配接器會讀取 BizTalk 訊息物件中的訊息內容以取得 Proxy 名稱，並呼叫關聯的外部 Web 服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-104">The SOAP send adapter reads the message context on the BizTalk Message object to get the proxy name and calls the associated external Web service proxy.</span></span>  
  
## <a name="client-authentication-for-the-soap-send-adapter"></a><span data-ttu-id="1b7fc-105">SOAP 傳送配接器的用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="1b7fc-105">Client Authentication for the SOAP Send Adapter</span></span>  
 <span data-ttu-id="1b7fc-106">SOAP 傳送配接器透過下列其中一種驗證類型，以目的地伺服器進行驗證：</span><span class="sxs-lookup"><span data-stu-id="1b7fc-106">The SOAP send adapter authenticates with the destination server by using one of the following authentication types:</span></span>  
  
-   <span data-ttu-id="1b7fc-107">**匿名的。**</span><span class="sxs-lookup"><span data-stu-id="1b7fc-107">**Anonymous.**</span></span> <span data-ttu-id="1b7fc-108">預設設定。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-108">The default setting.</span></span>  
  
-   <span data-ttu-id="1b7fc-109">**基本。**</span><span class="sxs-lookup"><span data-stu-id="1b7fc-109">**Basic.**</span></span> <span data-ttu-id="1b7fc-110">SOAP 連線會以純文字傳送使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-110">The SOAP connection sends the user name and password in plain text.</span></span>  
  
-   <span data-ttu-id="1b7fc-111">**摘要。**</span><span class="sxs-lookup"><span data-stu-id="1b7fc-111">**Digest.**</span></span> <span data-ttu-id="1b7fc-112">SOAP 連線以加密格式傳送使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-112">The SOAP connection sends the user name and password in an encrypted format.</span></span>  
  
-   <span data-ttu-id="1b7fc-113">**Kerberos 或 NTLM。**</span><span class="sxs-lookup"><span data-stu-id="1b7fc-113">**Kerberos or NTLM.**</span></span> <span data-ttu-id="1b7fc-114">使用者名稱或密碼都不會透過 SOAP 連線傳送。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-114">Neither the user name nor the password is sent over a SOAP connection.</span></span> <span data-ttu-id="1b7fc-115">SOAP 配接器永遠使用 SOAP 傳送配接器在其下執行此驗證類型的處理序之認證。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-115">The SOAP adapter always uses the credentials of the process under which the SOAP send adapter runs for this authentication type.</span></span>  
  
 <span data-ttu-id="1b7fc-116">此外，SOAP 傳送配接器可提供用戶端安全通訊端層 (SSL) 認證給 Web 伺服器 (若伺服器要求或接受)。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-116">Additionally, the SOAP send adapter can provide a client Secure Sockets Layer (SSL) certificate to the Web server if the server requires or accepts it.</span></span>  
  
 <span data-ttu-id="1b7fc-117">如果您啟用企業單一登入 (SSO)，當 SOAP 傳送配接器接收訊息的要求**SSOTicket**屬性，配接器連接到 SSO 伺服器以驗證及贖回票證。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-117">If you enabled Enterprise Single Sign-On (SSO), when the SOAP send adapter receives a message with the request to the **SSOTicket** property, the adapter connects to an SSO server to validate and redeem the ticket.</span></span> <span data-ttu-id="1b7fc-118">SOAP 配接器驗證票證後，會加密該票證，並從認證存放區擷取分支機構系統的認證。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-118">After the SOAP adapter validates the ticket, it is decrypted and the credentials for the affiliate system are retrieved from the credential store.</span></span> <span data-ttu-id="1b7fc-119">接著 SOAP 配接器會使用認證連接到分支機構系統，然後處理 SOAP 要求。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-119">The SOAP adapter then uses the credentials to connect to the affiliate system, and the SOAP request is processed.</span></span>  
  
## <a name="client-certificates-for-the-soap-send-adapter"></a><span data-ttu-id="1b7fc-120">SOAP 傳送配接器的用戶端認證</span><span class="sxs-lookup"><span data-stu-id="1b7fc-120">Client Certificates for the SOAP Send Adapter</span></span>  
 <span data-ttu-id="1b7fc-121">SOAP 傳送配接器可與接收或要求用戶端認證的伺服器建立安全連線。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-121">The SOAP send adapter can establish a secure connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="1b7fc-122">若指定用戶端認證，則與要求或接收用戶端認證的伺服器連線時，SOAP 傳送配接器會使用認證。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-122">If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="1b7fc-123">若沒有指定用戶端認證，且目的地伺服器要求用戶端認證，SOAP 傳送配接器就無法傳送訊息，且會依循標準重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-123">If you do not specify a client certificate and the destination server requires client certificates, the SOAP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="1b7fc-124">SOAP 傳送配接器使用的用戶端憑證所使用的帳戶之個人存放區中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-124">The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="1b7fc-125">SOAP 配接器會依照指紋來指定認證。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-125">The SOAP adapter specifies the certificate by its thumbprint.</span></span> <span data-ttu-id="1b7fc-126">若 SOAP 傳送配接器因為任何原因而無法載入認證，它所傳送的訊息就會擱置。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-126">If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
## <a name="negative-acknowledgement-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapters"></a><span data-ttu-id="1b7fc-127">HTTP 或 SOAP 配接器為失敗的傳輸產生的負值通知 (NACK) 訊息</span><span class="sxs-lookup"><span data-stu-id="1b7fc-127">Negative Acknowledgement (NACK) Messages Generated for Failed Transmissions by the HTTP or SOAP Adapters</span></span>  
 <span data-ttu-id="1b7fc-128">當訊息成功傳輸時，若啟用傳遞通知，BizTalk 傳訊引擎會發佈關聯的「通知」(ACK) 訊息到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-128">When a message is successfully transmitted, the BizTalk Messaging Engine publishes an associated Acknowledgement (ACK) message to the MessageBox database if delivery notifications are enabled.</span></span> <span data-ttu-id="1b7fc-129">同樣地，BizTalk 傳訊引擎擱置訊息或協調流程引擎擱置協調流程時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也會發佈關聯的「負值通知」(NACK) 訊息到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-129">Likewise, when a message is suspended by the BizTalk Messaging Engine or an orchestration is suspended by the orchestration engine, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publishes an associated Negative Acknowledgement (NACK) message to the MessageBox.</span></span> <span data-ttu-id="1b7fc-130">NACK 訊息包含內容屬性，以及由 SOAP 錯誤組成的訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-130">The NACK message contains context properties and a message body part consisting of a SOAP fault.</span></span> <span data-ttu-id="1b7fc-131">如果由於 HTTP 或 SOAP 配接器傳輸失敗而產生 NACK 訊息，則 SOAP 錯誤會包含**標頭**項目和**主體**目的地 Web 回應的項目伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-131">If the NACK message is generated due to a failed transmission from the HTTP or SOAP adapters, the SOAP fault contains the **Headers** element and the **Body** element of the response from the destination Web server.</span></span> <span data-ttu-id="1b7fc-132">以下範例是失敗的 SOAP 傳輸所產生的 NACK 中的 SOAP 錯誤：</span><span class="sxs-lookup"><span data-stu-id="1b7fc-132">The following is an example of the SOAP fault in a NACK generated for a failed SOAP transmission:</span></span>  
  
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
>  <span data-ttu-id="1b7fc-133">**標頭**項目和**主體**項目會限制為 48 KB。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-133">The **Headers** element and the **Body** element are limited to 48 KB.</span></span> <span data-ttu-id="1b7fc-134">**標頭**項目會四捨五入至最接近的完整標頭值組，但不超過限制。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-134">The **Headers** element is rounded to the nearest complete header value pair without exceeding the limit.</span></span> <span data-ttu-id="1b7fc-135">**主體**項目會截斷為 48 KB。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-135">The **Body** element is truncated to 48 KB.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b7fc-136">若 NACK 與 ACK 訊息沒有相符的訂閱，則會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-136">NACK and ACK messages are discarded if there are no matching subscriptions for them.</span></span> <span data-ttu-id="1b7fc-137">傳訊引擎不會擱置 NACK 及 ACK 訊息。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-137">NACK and ACK messages are not suspended by the Messaging Engine.</span></span>  
  
 <span data-ttu-id="1b7fc-138">若要訂閱 NACK 訊息，可以執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="1b7fc-138">To subscribe to a NACK message, you can do one of the following:</span></span>  
  
1.  <span data-ttu-id="1b7fc-139">使用適當訊息內容屬性的篩選建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-139">Create a send port with a filter for the appropriate message context property.</span></span> <span data-ttu-id="1b7fc-140">請參閱**訊息內容屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需系統訊息內容屬性的清單包括那些與訊息通知相關。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-140">See **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for a listing of system message context properties including those related to message acknowledgment.</span></span>  
  
2.  <span data-ttu-id="1b7fc-141">從標記為協調流程連接埠傳送**Delivery Notification = Transmitted**。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-141">Send from an orchestration port marked with **Delivery Notification = Transmitted**.</span></span> <span data-ttu-id="1b7fc-142">如果協調流程連接埠標示為**Delivery Notification = Transmitted**，協調流程會等候直到其接收到 ACK 或 NACK 傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-142">If an orchestration port is marked with **Delivery Notification = Transmitted**, the orchestration will wait until it receives either an ACK or a NACK for the message that was transmitted.</span></span> <span data-ttu-id="1b7fc-143">若產生的是 NACK，則會傳送到協調流程，且協調流程會擲回 DeliveryFailureException。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-143">If a NACK is generated then it will be routed to the orchestration and the orchestration will throw a DeliveryFailureException.</span></span> <span data-ttu-id="1b7fc-144">DeliveryFailureException 會從 NACK 訊息內文內包含的 SOAP 錯誤還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-144">The DeliveryFailureException is deserialized from the SOAP fault that is contained within the NACK message body.</span></span> <span data-ttu-id="1b7fc-145">若要從傳回協調流程的 SOAP 錯誤中擷取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，接著從 SOAP Detail 區段存取 InnerXml。</span><span class="sxs-lookup"><span data-stu-id="1b7fc-145">To retrieve the exception message string from the SOAP fault that is returned to the orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml from the SOAP Detail section.</span></span> <span data-ttu-id="1b7fc-146">下列程式碼範例示範如何執行此操作：</span><span class="sxs-lookup"><span data-stu-id="1b7fc-146">The following code sample demonstrates how to do this:</span></span>  
  
    ```  
    // Cast the DeliveryFailureException to a SoapException…  
    System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
    System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
    //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
    //object type created in an Exception handler  
    ```  
  
     <span data-ttu-id="1b7fc-147">上述程式碼範例傳回的 XML 片段應和下列類似：</span><span class="sxs-lookup"><span data-stu-id="1b7fc-147">The code sample above will return an XML fragment similar to the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b7fc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b7fc-148">See Also</span></span>  
 <span data-ttu-id="1b7fc-149">[什麼是 SOAP 配接器？](../core/what-is-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="1b7fc-149">[What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="1b7fc-150">SOAP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="1b7fc-150">SOAP Adapter Security Recommendations</span></span>](../core/soap-adapter-security-recommendations.md)