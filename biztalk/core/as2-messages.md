---
title: AS2 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fac8418-3c07-4513-94aa-e7a25087d789
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68ada5722e7b64d6ceaf3b511af5ac500a4dcce7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022596"
---
# <a name="as2-messages"></a>AS2 訊息
本主題說明 AS2 訊息，包括其結構、內容屬性和標頭。  
  
## <a name="structure-of-an-as2-message"></a>AS2 訊息的結構  
 在 BizTalk Server 中，AS2 訊息的結構是根據[RFC 4130 「 以 MIME 為基礎的安全端對端商務資料交換使用 HTTP、 Applicability Statement 2 (AS2)](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212))。  
  
 AS2 訊息的基本結構是由 HTTP 訊息內的 MIME 格式以及其他 AS2 專用標頭所組成。 HTTP、AS2 和 MIME 標頭下方訊息的特性會取決於訊息的類型：  
  
- **帶正負號**– 如果訊息經過簽署，文件內容周圍加入簽章包裝函式。  
  
- **壓縮**– 如果訊息已壓縮，文件和簽章內容周圍加入壓縮包裝函式。  
  
- **加密**– 如果訊息經過加密，文件、 簽章和壓縮內容周圍加入加密包裝函式。  
  
  下表將依據加密、簽章和壓縮，顯示 AS2 訊息的訊息結構。  
  
|AS2 訊息選項|訊息結構|  
|-------------------------|-----------------------|  
|-沒有壓縮<br /><br /> -沒有加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header      EDI/XML Payload`|  
|壓縮<br /><br /> -沒有加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           EDI/XML Payload (compressed)`|  
|簽章<br /><br /> -沒有壓縮<br /><br /> -沒有加密|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           EDI/XML Payload           CMS-PKCS7 Signature`|  
|簽章<br /><br /> 壓縮<br /><br /> -沒有加密|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|加密<br /><br /> -沒有壓縮<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           EDI/XML Payload (encrypted)`|  
|壓縮<br /><br /> 加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                EDI/XML Payload (compressed)(encrypted)`|  
|加密<br /><br /> 簽章<br /><br /> -沒有壓縮|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|壓縮<br /><br /> 加密<br /><br /> 簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
 如果文件內容是由多份文件所組成，它們會儲存在 multipart/related MIME 信封 RFC 2387 中所述。 Content-Disposition MIME 標頭可用來在訊息中指定每份文件的檔案名稱。  
  
 下表將依據訊息加密、簽章和壓縮選項，顯示包含多個附件之 AS2 訊息的訊息結構。  
  
|AS2 訊息選項|訊息結構|  
|-------------------------|-----------------------|  
|-沒有壓縮<br /><br /> -沒有加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header      MIME Multipart/related           EDI/XML Payloads`|  
|壓縮<br /><br /> -沒有加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           MIME Multipart/related                EDI/XML Payload (compressed)`|  
|簽章<br /><br /> -沒有壓縮<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           MIME Multipart/related                EDI/XML Payload           CMS-PKCS7 Signature`|  
|壓縮<br /><br /> 簽章<br /><br /> -沒有加密|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                MIME Multipart/related (compressed)                     EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|-加密<br /><br /> -沒有壓縮<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Multipart/related (encrypted)                EDI/XML Payload (encrypted)`|  
|壓縮<br /><br /> 加密<br /><br /> -沒有簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Multipart/related                     EDI/XML Payload (compressed)(encrypted)`|  
|加密<br /><br /> 簽章<br /><br /> -沒有壓縮|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                MIME Multipart/related                     EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|壓縮<br /><br /> 加密<br /><br /> 簽章|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     MIME Multipart/related                          EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
## <a name="as2-context-properties"></a>AS2 內容屬性  
 處理 AS2 訊息時使用的內容屬性包括可以升級的屬性，以及雖然不公開但是可以在擱置和追蹤訊息中檢視的屬性。 如需 AS2 內容屬性的清單，請參閱 < [AS2 內容屬性](../core/as2-context-properties.md)。  
  
## <a name="as2-headers"></a>AS2 標頭  
 AS2 訊息中的 AS2 標頭描述了接收和傳送合作對象，並提供接收合作對象傳送 MDN 回應所需的資訊。 接收的合作對象將使用 MDN 標頭，除非**使用協議設定進行驗證與 MDN 取代訊息標頭**屬性已在 AS2 協議中，選取或如果未提供協議中的資訊屬性。  
  
 AS2-From 標頭、AS2-To 標頭和 MessageID 內容屬性可唯一描述 AS2 訊息。 它們也可以用來將 MDN 與其對應的 AS2 訊息相互關聯。  
  
 下表列出這些標頭 (按字母順序排列)：  
  
|AS2 標頭|必要項目/選用項目|值|  
|----------------|------------------------|------------|  
|AS2-Version|選擇性|"1.1"|  
|AS2-From|必要項|傳送該 AS2 訊息的公司名稱。<br /><br /> 值：字串，可列印的 ASCII，長度為 1 到 128 個字元|  
|AS2-To|必要項|AS2 訊息傳送目標的公司名稱。<br /><br /> 值：字串，可列印的 ASCII，長度為 1 到 128 個字元|  
|AS2-Text|必要項|文字 (在訊息的這個標頭中)<br /><br /> 值：字串，可列印的 ASCII，長度為 1 到 128 個字元|  
|Disposition-Notification-To|必要項|存在時，可做為要傳回之 MDN 的要求。 如果伴隨著 Receipt-Delivery-Option 標頭，則為非同步 MDN 的要求， 否則便為同步 MDN 的要求。<br /><br /> 不存在時，就不需要 MDN。<br /><br /> 值：必須存在的郵件地址。 不過，此地址不能用來識別傳回 MDN 的位址。 接收端應用程式必須忽略郵件地址，而且不能投訴地址語法違規。|  
|EDIINT-Features|必要項|表示來源系統所支援的功能。 BizTalk 會使用這個標頭來指出支援多個附件。<br /><br /> 值：“MA”|  
|Receipt-Delivery-Option|必要項|指定 MDN 所應傳送的目的 URL。 當 Receipt-Delivery-Option 存在時，Disposition-Notification-To 便做為非同步 MDN 的要求。 Receipt-Delivery-Option 必須永遠伴隨著 Disposition-Notification-To。<br /><br /> 當 Receipt-Delivery-Option 不存在，而 Disposition-Notification-To 存在時，Disposition-Notification-To 則會做為同步 MDN 的要求。<br /><br /> 值：URL 字串。|  
|signed-receipt-protocol<br /><br /> （在配置通知選項）|選擇性|當設定為 "pcks7-signature" 時，可用來向接收合作對象要求簽署回條，並指定簽署回條應該傳回給要求者的格式。<br /><br /> 值：選用項目，pcks7-signature|  
|signed-receipt-micalg<br /><br /> （在配置通知選項）|選擇性|在簽署傳回的回條時，要求者所慣用的 MIC 演算法清單。 接收合作對象應該由左至右使用這份 MIC 演算法清單。<br /><br /> 值：選用項目，MD5 或 SHA1|  
  
 對於內送訊息，AS2EdiReceive 和 AS2Receive 接收管線會驗證 AS2 協議屬性中的簽署回條通訊協定和簽署回條 MIC 演算法。  
  
 對於外寄 AS2 訊息，AS2EdiSend 和 AS2Send 傳送管線會根據 AS2 協議中輸入的值，填入上述 AS2 標頭 (但 AS2-Version 除外，這個標頭已固定設定為 1.1)。  
  
 **MDN 要求**  
  
 要求接收合作對象傳回 MDN (訊息處理通知) 的方式是將下列標頭放在要傳送的訊息中：  
  
 MDN-request-header = "Disposition-notification-to"  ":"  mail-address  
  
 這個郵件地址不會用來識別傳回 MDN 的位址。 接收端應用程式必須忽略這個值，而且不能發佈有關地址語法違規的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [MDN 訊息](../core/mdn-messages.md)