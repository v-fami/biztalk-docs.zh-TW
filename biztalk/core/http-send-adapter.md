---
title: HTTP 傳送配接器 |Microsoft 文件
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
ms.openlocfilehash: ce8bfdfd380fac422f79ba175ae075a94f313dec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257974"
---
# <a name="http-send-adapter"></a>HTTP 傳送配接器
HTTP 傳送配接器會從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取得訊息，並在 HTTP POST 要求時，將它們傳送到目的地 URL。 HTTP 傳送配接器會從 BizTalk 訊息物件的內文部分取得訊息內容。 HTTP 傳送配接器會忽略 BizTalk 訊息物件中的所有其他部分。  
  
 在配接器傳送訊息到目的地 URL 且「BizTalk 傳訊引擎」收到 HTTP 成功狀態碼之後，HTTP 傳送配接器會從 MessageBox 資料庫刪除訊息。  
  
 在傳送埠上支援並可設定 HTTP 訊息的重新導向。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 裝載 HTTP 傳送配接器做為原生 BizTalk 應用程式。 它支援單向傳送訊息以及請求-回應傳輸。 HTTP 傳送配接器的傳送位置是透過傳送埠所設定的不同 URL。 此唯一 URL 可包含附加到基底 URL 的查詢字串。  
  
## <a name="batching-support-for-the-http-send-adapter"></a>HTTP 傳送配接器的批次支援  
 HTTP 傳送配接器不支援批次作業。  
  
## <a name="chunked-encoding-support-for-the-http-send-adapter"></a>HTTP 傳送配接器的區塊編碼支援  
 如果**啟用區塊編碼**已啟用組態選項，則 HTTP 傳送配接器傳送要求訊息使用區塊編碼，如果要求的大小超過 8 KB。 若已使用 HTTP Proxy 伺服器，則 HTTP 傳送配接器不會使用區塊編碼，並且永遠會在傳送之前處理資料。 **啟用區塊編碼**預設會啟用組態選項。  
  
 傳送配接器收到回應訊息時，可以接受有區塊編碼內文部分的回應訊息。  
  
## <a name="client-authentication-for-the-http-send-adapter"></a>HTTP 傳送配接器的用戶端驗證  
 HTTP 傳送配接器會使用下列其中一種驗證類型在目的地伺服器進行驗證：  
  
-   **匿名的。** HTTP 配接器不會傳送任何認證，連接到目的地伺服器時。 若目的地伺服器允許匿名驗證，則會使用在目的地伺服器上已設定之匿名帳戶的認證。  
  
-   **基本。** HTTP 配接器透過 HTTP 連線以純文字傳送使用者名稱與密碼。  
  
-   **摘要。** HTTP 配接器透過 HTTP 連線以加密格式傳送密碼。  
  
-   **Kerberos。** 不會透過 HTTP 連線傳送使用者名稱與密碼。 HTTP 配接器會使用 HTTP 傳送配接器在此程序之下執行此驗證類型的程序之認證。  
  
 此外，HTTP 傳送配接器還可以在伺服器要求或接受用戶端「安全通訊端層」(SSL) 憑證時，提供此憑證給 Web 伺服器。  
  
## <a name="client-certificates-for-the-http-send-adapter"></a>HTTP 傳送配接器的用戶端憑證  
 HTTP 傳送配接器可以與接受或要求用戶端憑證之伺服器建立安全連線。 若已指定用戶端憑證，則 HTTP 傳送配接器在與要求或接受用戶端憑證的伺服器連線時會使用憑證。 若未指定用戶端憑證，但目的地伺服器要求用戶端憑證，則 HTTP 傳送配接器無法傳送訊息並依照標準重試邏輯處理。  
  
 HTTP 傳送配接器會使用執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序的帳戶之個人存放區中的用戶端憑證。 憑證是由其指紋指定。 若 HTTP 傳送配接器因故無法載入憑證，則會擱置所傳送的訊息。  
  
## <a name="single-sign-on-support-for-the-http-adapter"></a>HTTP 配接器的單一登入支援  
 您可以使用 [BizTalk 管理] 主控台來設定「企業單一登入」(SSO)，以便與 HTTP 接收位置或傳送埠搭配使用。 本主題描述 SSO 如何與 HTTP 配接器搭配使用。  
  
 **單一登入 」 支援之 http 接收位置**  
  
 當 Microsoft Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。 Internet Server Application Programming Interface (ISAPI) 延伸模組會模擬 Microsoft Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。 此票證會儲存為**SSOTicket**中的訊息內容屬性。  
  
 在通過實例中，「BizTalk 傳訊引擎」會將訊息導向至 MessageBox 資料庫。 當配接器從 MessageBox 資料庫接收訊息時，HTTP 配接器呼叫**ISSOTicket.RedeemTicket 方法**具有加密票證及應用程式名稱，以擷取從後端認證SSO 存放區。 HTTP 配接器接著就會使用外部認證連接到後端系統並處理要求。 如需分支機構應用程式的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。  
  
 在協調流程叫用配接器的實例中，「BizTalk 傳訊引擎」會傳送此訊息至 MessageBox 資料庫。 協調流程應確保同時**SSOTicket**內容屬性和**Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID**包含票證的訊息內容屬性維護。 當配接器從 MessageBox 資料庫收到這個訊息時，配接器會呼叫**RedeemTicket**具有加密票證從 SSO 存放區擷取後端認證。 設計排程的使用者應該特別將此屬性複製到訊息中。  
  
 **HTTP 傳送配接器的單一登入支援**  
  
 如果已啟用 SSO，當 HTTP 傳送埠收到的訊息**Secure**屬性，它會呼叫 SSO 伺服器以驗證並贖回分支機構應用程式的票證。 分支機構應用程式的管理應用程式、分支機構系統管理員或 SSO 系統管理員可以呼叫 SSO 贖回票證。 接著 SSO 會解密票證並取得後端認證。 通過和協調流程實例與 HTTP 傳送埠相同。  
  
 依照預設，會停用 HTTP 傳送埠的 SSO。 如需啟用 SSO 的 HTTP 傳送埠的詳細資訊，請參閱[設定 HTTP 傳送埠](../core/configuring-an-http-send-port.md)。  
  
> [!NOTE]
>  您只能使用單一登入使用基本和摘要式驗證。  
  
 若要正確地實作 HTTP 接收配接器和傳送配接器的「單一登入」支援，必須符合下列條件：  
  
-   必須在下列各處指定相同的使用者帳戶：  
  
    -   IIS 虛擬目錄 (由 HTTP 接收配接器所監控) 之應用程式集區識別 (IIS 7.0) 或裝載 COM+ 應用程式識別。 如需有關設定 IIS 的 HTTP 接收位置，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
    -   HTTP 配接器正在執行中的外掛式主控的件執行個體所使用的登入認證。 如需如何設定主控件執行個體的登入認證資訊，請參閱[如何修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)。  
  
-   HTTP 配接器使用的外掛式主控件必須設定為 [信任的驗證]。 如需如何將主控件設定為信任的驗證資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
## <a name="negative-acknowledgment-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapter"></a>由 HTTP 或 SOAP 配接器為失敗傳輸產生的負值通知 (NACK) 訊息  
 當訊息已成功傳輸時，若已啟用 [傳遞通知]，則「BizTalk 傳訊引擎」會將相關的通知 (ACK) 訊息發佈到 MessageBox 中。 同樣的，當「BizTalk 傳訊引擎」擱置訊息或是協調流程引擎擱置協調流程時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將相關的負值通知 (NACK) 訊息發佈到 MessageBox。 NACK 訊息包含內容屬性以及由一個 SOAP 錯誤組成的訊息內文部分。 若 NACK 訊息是由於 HTTP 或 SOAP 配接器傳輸失敗而產生，則 SOAP 錯誤會包含來自目的地 Web 伺服器回應的標頭項目與內文項目。 下列範例是由於 HTTP 傳輸失敗而產生的 NACK 中的 SOAP 錯誤：  
  
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
>  標頭項目和內文項目限制為 48 KB。 標頭項目會四捨五入為最接近但不超過限制的完整標頭值組。 內文項目會截斷為 48 KB。  
  
> [!NOTE]
>  若 NACK 與 ACK 訊息沒有相符的訂閱，則會被捨棄。 「BizTalk 傳訊引擎」會擱置 NACK 與 ACK 訊息。  
  
 若要訂閱 NACK 訊息，可以執行下列其中一個動作：  
  
-   使用適當訊息內容屬性的篩選建立傳送埠。 請參閱**訊息內容屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需系統訊息內容屬性的清單包括那些與訊息通知相關。  
  
-   從標記為協調流程連接埠傳送**Delivery Notification = Transmitted**。 如果協調流程連接埠標示為**Delivery Notification = Transmitted**，協調流程會等候直到其接收到 ACK 或 NACK 傳輸訊息。 若產生的是 NACK，則會傳送到協調流程，且協調流程會擲回 DeliveryFailureException。 DeliveryFailureException 會從 NACK 訊息內文內包含的 SOAP 錯誤還原序列化。 若要從傳回協調流程的 SOAP 錯誤中擷取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，接著從 SOAP Detail 區段存取 InnerXml。 下列程式碼範例示範如何執行此操作：  
  
    ```  
    // Cast the DeliveryFailureException to a SoapException…  
    System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
    System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
    //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
    //object type created in an Exception handler  
  
    ```  
  
     上述程式碼範例傳回的 XML 片段應和下列類似：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [HTTP 配接器](../core/http-adapter.md)  
**SSO COM 物件**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]