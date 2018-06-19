---
title: HTTP 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9008833c-5a02-4fb4-a43e-09ca28a21eff
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f2f309a129c66d11d019b28b8ffc2b51d68e93d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710597"
---
# <a name="http-receive-adapter"></a><span data-ttu-id="86c9b-102">HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="86c9b-102">HTTP Receive Adapter</span></span>
<span data-ttu-id="86c9b-103">HTTP 接收配接器的接收位置是透過 BizTalk Server 管理主控台設定的不同 URL。</span><span class="sxs-lookup"><span data-stu-id="86c9b-103">The receive location for the HTTP receive adapter is a distinct URL configured through the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="86c9b-104">您可以為從用戶端執行的非同步提交或同步提交設定 HTTP 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="86c9b-104">You can configure the HTTP receive adapter for either asynchronous submission or synchronous submission from the client.</span></span> <span data-ttu-id="86c9b-105">非同步提交是單向提交，而同步提交則是雙向或要求-回應提交。</span><span class="sxs-lookup"><span data-stu-id="86c9b-105">Asynchronous submissions are one-way submissions and synchronous submissions are two way or request-response submissions.</span></span>  
  
 <span data-ttu-id="86c9b-106">您會使用 IIS 安全性來驗證和授權內送要求。</span><span class="sxs-lookup"><span data-stu-id="86c9b-106">You use IIS security for authentication and authorization of incoming requests.</span></span>  
  
## <a name="http-get-and-http-post-requests"></a><span data-ttu-id="86c9b-107">HTTP GET 與 HTTP POST 要求</span><span class="sxs-lookup"><span data-stu-id="86c9b-107">HTTP GET and HTTP POST Requests</span></span>  
 <span data-ttu-id="86c9b-108">HTTP 接收配接器可以接收訊息，以兩種方式，透過 HTTP POST 要求或 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="86c9b-108">The HTTP receive adapter can receive messages in two different ways—by an HTTP POST request or an HTTP GET request.</span></span>  
  
 <span data-ttu-id="86c9b-109">當 HTTP 接收配接器以 HTTP POST 要求接收訊息時，會發生以下一連串的事件：</span><span class="sxs-lookup"><span data-stu-id="86c9b-109">When an HTTP receive adapter gets messages on an HTTP POST request, the following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="86c9b-110">在 BizTalk Server 中設定的 URL 會在接收位置收到新訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-110">The URL configured in BizTalk Server receives a new message on the receive location.</span></span>  
  
2.  <span data-ttu-id="86c9b-111">接收配接器會建立「BizTalk 訊息」物件，以便將訊息提交至伺服器。</span><span class="sxs-lookup"><span data-stu-id="86c9b-111">The receive adapter creates a BizTalk Message object so that the message can be submitted to the server.</span></span>  
  
3.  <span data-ttu-id="86c9b-112">接收配接器建立 BizTalk 訊息物件只能有一個部分，內文部分。</span><span class="sxs-lookup"><span data-stu-id="86c9b-112">The receive adapter creates the BizTalk Message object with only one part—the body part.</span></span>  
  
4.  <span data-ttu-id="86c9b-113">在已讀取訊息並成功提交至伺服器之後，HTTP 接收配接器會將 HTTP 代碼 202 傳回表示已接收要求的用戶端。</span><span class="sxs-lookup"><span data-stu-id="86c9b-113">After the message has been read and successfully submitted to the server, the HTTP receive adapter sends an HTTP code 202 back to the client indicating that the request was accepted.</span></span>  
  
     <span data-ttu-id="86c9b-114">此外，HTTP 接收配接器可以在 HTTP 回應時傳送訊息相互關聯 Token。</span><span class="sxs-lookup"><span data-stu-id="86c9b-114">Optionally, the HTTP receive adapter can send a message correlation token on the HTTP response.</span></span> <span data-ttu-id="86c9b-115">這個相互關聯 Token 代表 BizTalk Server 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-115">This correlation token represents the message within BizTalk Server.</span></span> <span data-ttu-id="86c9b-116">若 HTTP 接收位置是在要求-回應連接埠中，配接器會傳回成功碼 200 及回應訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-116">If the HTTP receive location is in a request-response port, the adapter returns success code 200 along with the response message.</span></span>  
  
 <span data-ttu-id="86c9b-117">當 HTTP 接收配接器處理來自 HTTP GET 要求的訊息時，接收配接器會建立「BizTalk 訊息」物件，並將 HTTP GET 要求的解譯查詢字串放入 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="86c9b-117">When an HTTP receive adapter processes messages from an HTTP GET request, the receive adapter creates a BizTalk Message object and puts the decoded query string of the HTTP GET request into the BizTalk message body part.</span></span> <span data-ttu-id="86c9b-118">HTTP 配接器會使用下列演算法，來選取要放入 BizTalk 訊息內文部分的查詢字串：</span><span class="sxs-lookup"><span data-stu-id="86c9b-118">The HTTP adapter selects the query string that is placed into the BizTalk message body part using the following algorithm:</span></span>  
  
-   <span data-ttu-id="86c9b-119">若 HTTP 接收配接器接收的 HTTP GET 要求，它內送 URI 字串分割成兩個部分，做為分隔符號使用問號 （？） 符號。</span><span class="sxs-lookup"><span data-stu-id="86c9b-119">If the HTTP receive adapter receives an HTTP GET request, it splits the incoming URI string into two parts, using the question mark (?) symbol as a delimiter.</span></span>  
  
-   <span data-ttu-id="86c9b-120">URI 字串，在問號分隔符號之前的部分的第一個部分會複製到 **InboundTransportLocation** 訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="86c9b-120">The first part of the URI string, the part before the question mark delimiter, is copied into the **InboundTransportLocation** property on the message context.</span></span> <span data-ttu-id="86c9b-121">**InboundTransportLocation** 屬性可唯一識別 BizTalk Server 接收訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="86c9b-121">The **InboundTransportLocation** property uniquely identifies the location where BizTalk Server received the message.</span></span> <span data-ttu-id="86c9b-122">引擎會使用此屬性，來決定要為訊息執行哪一個接收位置。</span><span class="sxs-lookup"><span data-stu-id="86c9b-122">The engine uses this property to determine which receive location to run for the message.</span></span>  
  
-   <span data-ttu-id="86c9b-123">HTTP 配接器接受其餘的 URI 字串，即問號分隔符號，後面的部分和解碼，並將它複製到 BizTalk 訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="86c9b-123">The HTTP adapter takes the rest of the URI string, the part after the question mark delimiter, and decodes and copies it into the BizTalk message body part.</span></span>  
  
-   <span data-ttu-id="86c9b-124">若 HTTP 接收配接器收到空的 HTTP GET 或 HTTP POST 作業，就會拒絕它。</span><span class="sxs-lookup"><span data-stu-id="86c9b-124">If an empty HTTP GET or HTTP POST operation is received by the HTTP receive adapter, it is rejected.</span></span>  
  
## <a name="http-receive-adapter-processing-of-a-get-request"></a><span data-ttu-id="86c9b-125">GET 要求的 HTTP 接收配接器處理</span><span class="sxs-lookup"><span data-stu-id="86c9b-125">HTTP Receive Adapter Processing of a GET Request</span></span>  
 <span data-ttu-id="86c9b-126">以下範例將顯示 HTTP 接收配接器如何處理 HTTP GET 要求收到的訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-126">The following are examples of how the HTTP receive adapter processes messages received by HTTP GET requests.</span></span> <span data-ttu-id="86c9b-127">這些範例假設 HTTP 接收配接器是使用下列兩個接收位置來設定：</span><span class="sxs-lookup"><span data-stu-id="86c9b-127">These examples assume that the HTTP receive adapter is configured with the following two receive locations:</span></span>  
  
```  
/vroot/BTSHTTPReceive.dll  
/vroot/BTSHTTPReceive.dll?LocationID=1  
```  
  
1.  <span data-ttu-id="86c9b-128">假設用戶端的 HTTP GET 要求如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-128">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1  
    ```  
  
     <span data-ttu-id="86c9b-129">HTTP 接收配接器採取的動作如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-129">The action taken by the HTTP receive adapter is as follows:</span></span>  
  
     <span data-ttu-id="86c9b-130">設定 **InboundTransportLocation** 屬性在訊息內容等於 /vroot/BTSHTTPReceive.dll，以及 BizTalk 訊息物件內文部分為 LocationID = 1。</span><span class="sxs-lookup"><span data-stu-id="86c9b-130">Set the **InboundTransportLocation** property on the message context equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1.</span></span>  
  
2.  <span data-ttu-id="86c9b-131">假設用戶端的 HTTP GET 要求如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-131">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1&MyParam=My%20Value  
    ```  
  
     <span data-ttu-id="86c9b-132">HTTP 接收配接器採取的動作如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-132">The action taken by the HTTP receive adapter is as follows:</span></span>  
  
     <span data-ttu-id="86c9b-133">設定 **InboundTransportLocation** 屬性等於 /vroot/BTSHTTPReceive.dll，以及 BizTalk 訊息物件內文部分設為 LocationID = 1&myparam = My Value。</span><span class="sxs-lookup"><span data-stu-id="86c9b-133">Set the **InboundTransportLocation** property equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1&MyParam=My Value.</span></span>  
  
3.  <span data-ttu-id="86c9b-134">假設用戶端的 HTTP GET 要求如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-134">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll  
    ```  
  
     <span data-ttu-id="86c9b-135">HTTP 接收配接器採取的動作如下：</span><span class="sxs-lookup"><span data-stu-id="86c9b-135">The action taken by the HTTP receive adapter is+ as follows:</span></span>  
  
     <span data-ttu-id="86c9b-136">拒絕由於 HTTP GET 要求格式不正確而發出的要求。</span><span class="sxs-lookup"><span data-stu-id="86c9b-136">Reject the request due to incorrect formatting of the HTTP GET request.</span></span>  
  
## <a name="batching-support-for-the-http-receive-adapter"></a><span data-ttu-id="86c9b-137">HTTP 接收配接器的批次支援</span><span class="sxs-lookup"><span data-stu-id="86c9b-137">Batching Support for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="86c9b-138">HTTP 接收配接器會將訊息以批次方式提交至伺服器。</span><span class="sxs-lookup"><span data-stu-id="86c9b-138">The HTTP receive adapter submits messages to the server in batches.</span></span> <span data-ttu-id="86c9b-139">用以提交訊息至伺服器的批次大小，可在 HTTP 配接器接收處理常式上設定。</span><span class="sxs-lookup"><span data-stu-id="86c9b-139">The size of the batch used to submit messages to the server can be configured on the HTTP adapter receive handler.</span></span>  
  
## <a name="http-receive-adapter-support-for-suspending-failed-requests"></a><span data-ttu-id="86c9b-140">HTTP 接收配接器支援擱置失敗的要求</span><span class="sxs-lookup"><span data-stu-id="86c9b-140">HTTP Receive Adapter Support for Suspending Failed Requests</span></span>  
 <span data-ttu-id="86c9b-141">BizTalk Server HTTP 接收配接器已組態設定，**擱置失敗的要求**，以控制發生什麼情況的 HTTP 要求與接收管線失敗、 對應失敗，因為輸入的處理失敗或路由失敗。</span><span class="sxs-lookup"><span data-stu-id="86c9b-141">The BizTalk Server HTTP receive adapter has a configuration setting, **Suspend Failed Requests**, to control what happens with an HTTP request if it fails inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="86c9b-142">此設定有兩個可能的值：</span><span class="sxs-lookup"><span data-stu-id="86c9b-142">The setting has two possible values:</span></span>  
  
-   <span data-ttu-id="86c9b-143">**值為 false。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-143">**False.**</span></span> <span data-ttu-id="86c9b-144">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="86c9b-144">This is the default setting.</span></span> <span data-ttu-id="86c9b-145">HTTP 接收配接器會捨棄因接收管線失敗、對應失敗或路由傳送失敗，而造成輸入處理失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-145">The HTTP receive adapter discards messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="86c9b-146">此外，會傳送錯誤狀態碼 401 或 500 至用戶端。</span><span class="sxs-lookup"><span data-stu-id="86c9b-146">Additionally, an error status code 401 or 500 is sent to the client.</span></span> 
  
-   <span data-ttu-id="86c9b-147">**則為 true。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-147">**True.**</span></span> <span data-ttu-id="86c9b-148">HTTP 接收配接器會擱置因接收管線失敗、對應失敗或路由傳送失敗，而造成輸入處理失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-148">The HTTP receive adapter suspends messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="86c9b-149">針對單向接收埠 **已接受** 狀態碼 202 傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="86c9b-149">For one-way receive ports an **Accepted** status code 202 is sent to the client.</span></span> <span data-ttu-id="86c9b-150">針對雙向接收埠 **錯誤** 狀態碼 500 傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="86c9b-150">For two-way receive ports an **Error** status code 500 is sent to the client.</span></span>  
  
## <a name="chunked-encoding-support-for-the-http-receive-adapter"></a><span data-ttu-id="86c9b-151">HTTP 接收配接器的區塊編碼支援</span><span class="sxs-lookup"><span data-stu-id="86c9b-151">Chunked Encoding Support for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="86c9b-152">HTTP 接收配接器會接受含有區塊編碼內文訊息的 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="86c9b-152">The HTTP receive adapter accepts HTTP requests with chunked encoded body messages.</span></span> <span data-ttu-id="86c9b-153">接收配接器會使用區塊編碼，來傳送內文大小大於 4 KB 的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-153">The receive adapter uses chunked encoding to send response messages when the body size is larger than 4 KB.</span></span> <span data-ttu-id="86c9b-154">區塊編碼可以關閉藉由設定中所述的 DWORD 登錄項目[HTTP 配接器組態和調整參數](../core/http-adapter-configuration-and-tuning-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="86c9b-154">Chunked encoding can be turned off by setting the DWORD registry entry described in [HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md)</span></span>  
  
## <a name="client-certificates-for-the-http-receive-adapter"></a><span data-ttu-id="86c9b-155">HTTP 接收配接器的用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="86c9b-155">Client Certificates for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="86c9b-156">只要為 HTTP 接收位置使用具有用戶端憑證的安全連線，HTTP 接收配接器就會從 Microsoft Internet Information Services (IIS) 取得用戶端憑證指紋，並將它新增至該位置上透過 HTTP 接收之所有訊息的訊息內容中。</span><span class="sxs-lookup"><span data-stu-id="86c9b-156">Whenever a secure connection with a client certificate is used for the HTTP receive location, the HTTP receive adapter obtains the client certificate thumbprint from Microsoft Internet Information Services (IIS) and adds it to the message context of all messages that were received over HTTPS on that location.</span></span> <span data-ttu-id="86c9b-157">HTTP 接收配接器會設定下列的系統屬性：</span><span class="sxs-lookup"><span data-stu-id="86c9b-157">The HTTP receive adapter sets the following system properties:</span></span>  
  
```  
SourcePartyEvidenceQualifier = "Certificate"  
SourcePartyEvidence = <certificate thumbprint>  
```  
  
## <a name="status-codes-returned-by-the-http-receive-adapter"></a><span data-ttu-id="86c9b-158">HTTP 接收配接器傳回的狀態碼</span><span class="sxs-lookup"><span data-stu-id="86c9b-158">Status Codes Returned by the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="86c9b-159">下列清單包含 HTTP 接收配接器所傳回的狀態碼。</span><span class="sxs-lookup"><span data-stu-id="86c9b-159">The following list contains status codes returned by the HTTP receive adapter.</span></span>  
  
-   <span data-ttu-id="86c9b-160">**200 確定。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-160">**200 OK.**</span></span> <span data-ttu-id="86c9b-161">配接器已成功處理要求訊息並產生回應。</span><span class="sxs-lookup"><span data-stu-id="86c9b-161">The adapter successfully processed the request message and generated a response.</span></span> <span data-ttu-id="86c9b-162">配接器會從 HTTP 要求-回應連接埠傳回 HTTP 回應的狀態碼。</span><span class="sxs-lookup"><span data-stu-id="86c9b-162">The adapter returns this status code on the HTTP response from the HTTP request-response port.</span></span>  
  
-   <span data-ttu-id="86c9b-163">**202 已接受訊息。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-163">**202 Message Accepted.**</span></span> <span data-ttu-id="86c9b-164">配接器已成功將訊息提交至伺服器，或是已擱置單向要求。</span><span class="sxs-lookup"><span data-stu-id="86c9b-164">The adapter successfully submitted the message into the server or a one-way request is suspended.</span></span> <span data-ttu-id="86c9b-165">配接器會從單向 HTTP 接收埠傳回 HTTP 回應的此狀態碼。</span><span class="sxs-lookup"><span data-stu-id="86c9b-165">The adapter returns this status code on the HTTP response from a one way HTTP receive port.</span></span>  
  
-   <span data-ttu-id="86c9b-166">**401 拒絕存取。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-166">**401 Access Denied.**</span></span> <span data-ttu-id="86c9b-167">在需要驗證的接收埠上接收了 HTTP 要求，但該訊息的安全性檢查失敗。</span><span class="sxs-lookup"><span data-stu-id="86c9b-167">The HTTP request is received on an authentication-required receive port and the security check for that message failed.</span></span> <span data-ttu-id="86c9b-168">例如，無法解析合作對象或是未解密訊息。</span><span class="sxs-lookup"><span data-stu-id="86c9b-168">For example, the party was not resolved or the message was not decrypted.</span></span>  
  
-   <span data-ttu-id="86c9b-169">**500 內部伺服器錯誤。**</span><span class="sxs-lookup"><span data-stu-id="86c9b-169">**500 Internal Server Error.**</span></span> <span data-ttu-id="86c9b-170">處理 HTTP 要求的一般失敗。</span><span class="sxs-lookup"><span data-stu-id="86c9b-170">A general failure to process the HTTP request.</span></span> <span data-ttu-id="86c9b-171">除非訊息不由 BizTalk Server 擱置的組態設定 **擱置失敗的要求** 設為 **True** 在雙向接收埠。</span><span class="sxs-lookup"><span data-stu-id="86c9b-171">The message is not suspended by BizTalk Server unless the configuration setting **Suspend Failed Requests** is set to **True** for a two-way receive port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c9b-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86c9b-172">See Also</span></span>  
 [<span data-ttu-id="86c9b-173">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="86c9b-173">HTTP Adapter</span></span>](../core/http-adapter.md)