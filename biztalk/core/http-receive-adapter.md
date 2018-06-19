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
# <a name="http-receive-adapter"></a>HTTP 接收配接器
HTTP 接收配接器的接收位置是透過 BizTalk Server 管理主控台設定的不同 URL。  
  
 您可以為從用戶端執行的非同步提交或同步提交設定 HTTP 接收配接器。 非同步提交是單向提交，而同步提交則是雙向或要求-回應提交。  
  
 您會使用 IIS 安全性來驗證和授權內送要求。  
  
## <a name="http-get-and-http-post-requests"></a>HTTP GET 與 HTTP POST 要求  
 HTTP 接收配接器可以接收訊息，以兩種方式，透過 HTTP POST 要求或 HTTP GET 要求。  
  
 當 HTTP 接收配接器以 HTTP POST 要求接收訊息時，會發生以下一連串的事件：  
  
1.  在 BizTalk Server 中設定的 URL 會在接收位置收到新訊息。  
  
2.  接收配接器會建立「BizTalk 訊息」物件，以便將訊息提交至伺服器。  
  
3.  接收配接器建立 BizTalk 訊息物件只能有一個部分，內文部分。  
  
4.  在已讀取訊息並成功提交至伺服器之後，HTTP 接收配接器會將 HTTP 代碼 202 傳回表示已接收要求的用戶端。  
  
     此外，HTTP 接收配接器可以在 HTTP 回應時傳送訊息相互關聯 Token。 這個相互關聯 Token 代表 BizTalk Server 中的訊息。 若 HTTP 接收位置是在要求-回應連接埠中，配接器會傳回成功碼 200 及回應訊息。  
  
 當 HTTP 接收配接器處理來自 HTTP GET 要求的訊息時，接收配接器會建立「BizTalk 訊息」物件，並將 HTTP GET 要求的解譯查詢字串放入 BizTalk 訊息內文部分。 HTTP 配接器會使用下列演算法，來選取要放入 BizTalk 訊息內文部分的查詢字串：  
  
-   若 HTTP 接收配接器接收的 HTTP GET 要求，它內送 URI 字串分割成兩個部分，做為分隔符號使用問號 （？） 符號。  
  
-   URI 字串，在問號分隔符號之前的部分的第一個部分會複製到 **InboundTransportLocation** 訊息內容屬性。 **InboundTransportLocation** 屬性可唯一識別 BizTalk Server 接收訊息的位置。 引擎會使用此屬性，來決定要為訊息執行哪一個接收位置。  
  
-   HTTP 配接器接受其餘的 URI 字串，即問號分隔符號，後面的部分和解碼，並將它複製到 BizTalk 訊息內文部分。  
  
-   若 HTTP 接收配接器收到空的 HTTP GET 或 HTTP POST 作業，就會拒絕它。  
  
## <a name="http-receive-adapter-processing-of-a-get-request"></a>GET 要求的 HTTP 接收配接器處理  
 以下範例將顯示 HTTP 接收配接器如何處理 HTTP GET 要求收到的訊息。 這些範例假設 HTTP 接收配接器是使用下列兩個接收位置來設定：  
  
```  
/vroot/BTSHTTPReceive.dll  
/vroot/BTSHTTPReceive.dll?LocationID=1  
```  
  
1.  假設用戶端的 HTTP GET 要求如下：  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1  
    ```  
  
     HTTP 接收配接器採取的動作如下：  
  
     設定 **InboundTransportLocation** 屬性在訊息內容等於 /vroot/BTSHTTPReceive.dll，以及 BizTalk 訊息物件內文部分為 LocationID = 1。  
  
2.  假設用戶端的 HTTP GET 要求如下：  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1&MyParam=My%20Value  
    ```  
  
     HTTP 接收配接器採取的動作如下：  
  
     設定 **InboundTransportLocation** 屬性等於 /vroot/BTSHTTPReceive.dll，以及 BizTalk 訊息物件內文部分設為 LocationID = 1&myparam = My Value。  
  
3.  假設用戶端的 HTTP GET 要求如下：  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll  
    ```  
  
     HTTP 接收配接器採取的動作如下：  
  
     拒絕由於 HTTP GET 要求格式不正確而發出的要求。  
  
## <a name="batching-support-for-the-http-receive-adapter"></a>HTTP 接收配接器的批次支援  
 HTTP 接收配接器會將訊息以批次方式提交至伺服器。 用以提交訊息至伺服器的批次大小，可在 HTTP 配接器接收處理常式上設定。  
  
## <a name="http-receive-adapter-support-for-suspending-failed-requests"></a>HTTP 接收配接器支援擱置失敗的要求  
 BizTalk Server HTTP 接收配接器已組態設定，**擱置失敗的要求**，以控制發生什麼情況的 HTTP 要求與接收管線失敗、 對應失敗，因為輸入的處理失敗或路由失敗。 此設定有兩個可能的值：  
  
-   **值為 false。** 這是預設值。 HTTP 接收配接器會捨棄因接收管線失敗、對應失敗或路由傳送失敗，而造成輸入處理失敗的訊息。 此外，會傳送錯誤狀態碼 401 或 500 至用戶端。 
  
-   **則為 true。** HTTP 接收配接器會擱置因接收管線失敗、對應失敗或路由傳送失敗，而造成輸入處理失敗的訊息。 針對單向接收埠 **已接受** 狀態碼 202 傳送至用戶端。 針對雙向接收埠 **錯誤** 狀態碼 500 傳送至用戶端。  
  
## <a name="chunked-encoding-support-for-the-http-receive-adapter"></a>HTTP 接收配接器的區塊編碼支援  
 HTTP 接收配接器會接受含有區塊編碼內文訊息的 HTTP 要求。 接收配接器會使用區塊編碼，來傳送內文大小大於 4 KB 的回應訊息。 區塊編碼可以關閉藉由設定中所述的 DWORD 登錄項目[HTTP 配接器組態和調整參數](../core/http-adapter-configuration-and-tuning-parameters.md)  
  
## <a name="client-certificates-for-the-http-receive-adapter"></a>HTTP 接收配接器的用戶端憑證  
 只要為 HTTP 接收位置使用具有用戶端憑證的安全連線，HTTP 接收配接器就會從 Microsoft Internet Information Services (IIS) 取得用戶端憑證指紋，並將它新增至該位置上透過 HTTP 接收之所有訊息的訊息內容中。 HTTP 接收配接器會設定下列的系統屬性：  
  
```  
SourcePartyEvidenceQualifier = "Certificate"  
SourcePartyEvidence = <certificate thumbprint>  
```  
  
## <a name="status-codes-returned-by-the-http-receive-adapter"></a>HTTP 接收配接器傳回的狀態碼  
 下列清單包含 HTTP 接收配接器所傳回的狀態碼。  
  
-   **200 確定。** 配接器已成功處理要求訊息並產生回應。 配接器會從 HTTP 要求-回應連接埠傳回 HTTP 回應的狀態碼。  
  
-   **202 已接受訊息。** 配接器已成功將訊息提交至伺服器，或是已擱置單向要求。 配接器會從單向 HTTP 接收埠傳回 HTTP 回應的此狀態碼。  
  
-   **401 拒絕存取。** 在需要驗證的接收埠上接收了 HTTP 要求，但該訊息的安全性檢查失敗。 例如，無法解析合作對象或是未解密訊息。  
  
-   **500 內部伺服器錯誤。** 處理 HTTP 要求的一般失敗。 除非訊息不由 BizTalk Server 擱置的組態設定 **擱置失敗的要求** 設為 **True** 在雙向接收埠。  
  
## <a name="see-also"></a>另請參閱  
 [HTTP 配接器](../core/http-adapter.md)