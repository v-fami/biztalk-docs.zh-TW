---
title: "SOAP 傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d65218d-516b-4e45-a824-272ef6ef298c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f59babb164458f7a5d072809d038fb253482553d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-send-adapter"></a>SOAP 傳送配接器
您可以使用 SOAP 傳送配接器來呼叫 Web 服務。 SOAP 傳送配接器會讀取 BizTalk 訊息物件中的訊息內容以取得 Proxy 名稱，並呼叫關聯的外部 Web 服務 Proxy。  
  
## <a name="client-authentication-for-the-soap-send-adapter"></a>SOAP 傳送配接器的用戶端驗證  
 SOAP 傳送配接器透過下列其中一種驗證類型，以目的地伺服器進行驗證：  
  
-   **匿名的。** 預設設定。  
  
-   **基本。** SOAP 連線會以純文字傳送使用者名稱及密碼。  
  
-   **摘要。** SOAP 連線以加密格式傳送使用者名稱及密碼。  
  
-   **Kerberos 或 NTLM。** 使用者名稱或密碼都不會透過 SOAP 連線傳送。 SOAP 配接器永遠使用 SOAP 傳送配接器在其下執行此驗證類型的處理序之認證。  
  
 此外，SOAP 傳送配接器可提供用戶端安全通訊端層 (SSL) 認證給 Web 伺服器 (若伺服器要求或接受)。  
  
 如果您啟用企業單一登入 (SSO)，當 SOAP 傳送配接器接收訊息的要求**SSOTicket**屬性，配接器連接到 SSO 伺服器以驗證及贖回票證。 SOAP 配接器驗證票證後，會加密該票證，並從認證存放區擷取分支機構系統的認證。 接著 SOAP 配接器會使用認證連接到分支機構系統，然後處理 SOAP 要求。  
  
## <a name="client-certificates-for-the-soap-send-adapter"></a>SOAP 傳送配接器的用戶端認證  
 SOAP 傳送配接器可與接收或要求用戶端認證的伺服器建立安全連線。 若指定用戶端認證，則與要求或接收用戶端認證的伺服器連線時，SOAP 傳送配接器會使用認證。 若沒有指定用戶端認證，且目的地伺服器要求用戶端認證，SOAP 傳送配接器就無法傳送訊息，且會依循標準重試邏輯。  
  
 SOAP 傳送配接器使用的用戶端憑證所使用的帳戶之個人存放區中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。 SOAP 配接器會依照指紋來指定認證。 若 SOAP 傳送配接器因為任何原因而無法載入認證，它所傳送的訊息就會擱置。  
  
## <a name="negative-acknowledgement-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapters"></a>HTTP 或 SOAP 配接器為失敗的傳輸產生的負值通知 (NACK) 訊息  
 當訊息成功傳輸時，若啟用傳遞通知，BizTalk 傳訊引擎會發佈關聯的「通知」(ACK) 訊息到 MessageBox 資料庫。 同樣地，BizTalk 傳訊引擎擱置訊息或協調流程引擎擱置協調流程時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也會發佈關聯的「負值通知」(NACK) 訊息到 MessageBox。 NACK 訊息包含內容屬性，以及由 SOAP 錯誤組成的訊息內文部分。 如果由於 HTTP 或 SOAP 配接器傳輸失敗而產生 NACK 訊息，則 SOAP 錯誤會包含**標頭**項目和**主體**目的地 Web 回應的項目伺服器。 以下範例是失敗的 SOAP 傳輸所產生的 NACK 中的 SOAP 錯誤：  
  
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
>  **標頭**項目和**主體**項目會限制為 48 KB。 **標頭**項目會四捨五入至最接近的完整標頭值組，但不超過限制。 **主體**項目會截斷為 48 KB。  
  
> [!NOTE]
>  若 NACK 與 ACK 訊息沒有相符的訂閱，則會被捨棄。 傳訊引擎不會擱置 NACK 及 ACK 訊息。  
  
 若要訂閱 NACK 訊息，可以執行下列其中一個動作：  
  
1.  使用適當訊息內容屬性的篩選建立傳送埠。 請參閱**訊息內容屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需系統訊息內容屬性的清單包括那些與訊息通知相關。  
  
2.  從標記為協調流程連接埠傳送**Delivery Notification = Transmitted**。 如果協調流程連接埠標示為**Delivery Notification = Transmitted**，協調流程會等候直到其接收到 ACK 或 NACK 傳輸訊息。 若產生的是 NACK，則會傳送到協調流程，且協調流程會擲回 DeliveryFailureException。 DeliveryFailureException 會從 NACK 訊息內文內包含的 SOAP 錯誤還原序列化。 若要從傳回協調流程的 SOAP 錯誤中擷取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，接著從 SOAP Detail 區段存取 InnerXml。 下列程式碼範例示範如何執行此操作：  
  
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
 [什麼是 SOAP 配接器？](../core/what-is-the-soap-adapter.md)   
 [SOAP 配接器安全性建議](../core/soap-adapter-security-recommendations.md)