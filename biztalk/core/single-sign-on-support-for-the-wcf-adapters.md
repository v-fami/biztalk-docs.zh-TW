---
title: 單一登入支援 WCF 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF adapters, Single Sign-On
- Single Sign-On, WCF adapters
ms.assetid: 70a33d87-50bd-41de-9084-68dd66b0dbf9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 712aa01190762d6c6f74604a5f48c19fe42531d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280054"
---
# <a name="single-sign-on-support-for-the-wcf-adapters"></a>WCF 配接器的單一登入支援
您可以使用 BizTalk 管理主控台來設定「企業單一登入」(SSO)，以便與 WCF 接收位置或傳送埠搭配使用。 本主題將說明 SSO 如何與 WCF 配接器搭配使用。  
  
 在使用者會與各式各樣的系統和應用程式互動的企業環境中，這個環境不大可能會針對多重程序、產品和電腦的整個期間維護使用者的內容。 這類使用者內容是提供單一登入能力的重要資訊，因為在確認是誰發出原始要求時必須用到這份資訊。 為了解決這個問題，「企業單一登入」(SSO) 提供了 SSO 票證 (非 Kerberos 票證)，應用程式可以用來取得對應提出原始要求之使用者的認證。  
  
 當接收配接器收到訊息時，該配接器可能會要求來自 SSO 伺服器的 SSO 票證。 這個加密票證包含發出要求和逾時期限之使用者的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 識別。 取得票證之後，票證會當成屬性新增至內送訊息。 當傳送配接器傳輸訊息時，配接器會在連絡 SSO 伺服器時使用已發出的 SSO 票證，以及配接器將用來擷取認證的分支機構應用程式名稱。 SSO 伺服器會查詢目標分支機構應用程式的使用者認證，然後將該認證傳回給傳送配接器，由它使用認證，將已經過適當驗證的訊息傳送到該分支機構應用程式。  
  
## <a name="single-sign-on-support-for-the-wcf-receive-locations"></a>WCF 接收位置的單一登入支援  
 所套用的安全性設定，再加上接收位置所使用的 WCF 配接器類型，就會決定 WCF 接收配接器是否可以發出 SSO 票證。 對於要發出 SSO 票證的 WCF 接收配接器，WCF 用戶端必須傳送該配接器可以模擬的認證。 「模擬」(Impersonation) 是伺服器應用程式處理該用戶端識別的能力。 認證必須對應到有效的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 使用者帳戶，才可以達到適當的模擬。  
  
> [!NOTE]
>  對於不要求用戶端傳送用於模擬之認證的安全性設定和 WCF 配接器，您在發出 SSO 票證時可以透過用戶端可用自訂接收管線元件傳送的任何認證類型。 如需有關如何處理 SSO 票證的接收管線元件，請參閱範例管線元件，InPipelineComp 納入[服務導向解決方案的檔案庫存](../core/file-inventory-for-the-service-oriented-solution.md)。  
  
 **單一登入支援 Wcf-basichttp 接收位置**  
  
 WCF-BasicHttp 接收配接器可以從 SSO 伺服器發出 SSO 票證，但是只能在下表顯示的安全性組態中。  
  
> [!NOTE]
>  如需有關將憑證對應到[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]使用者帳戶，請參閱 < 對應憑證至使用者帳戶 >，網址[http://go.microsoft.com/fwlink/?LinkId=87478](http://go.microsoft.com/fwlink/?LinkId=87478)。  
  
|安全性模式|傳輸用戶端認證類型|[憑證]|  
|-------------------|--------------------------------------|------------------------------------|  
|傳輸|Basic|不適用|  
|傳輸|Digest|不適用|  
|傳輸|Ntlm|不適用|  
|傳輸|Windows|不適用|  
|傳輸|憑證|不適用|  
|訊息|不適用|UserName|  
|訊息|不適用|憑證|  
|TransportWithMessageCredential|不適用|憑證|  
|TransportWithMessageCredential|不適用|UserName|  
|TransportCredentialOnly|Basic|不適用|  
|TransportCredentialOnly|Digest|不適用|  
|TransportCredentialOnly|Ntlm|不適用|  
|TransportCredentialOnly|Windows|不適用|  
|TransportCredentialOnly|憑證|不適用|  
  
 **單一登入 」 支援針對 Wcf-wshttp 接收位置**  
  
 WCF-WSHttp 接收配接器可以從 SSO 伺服器發行 SSO 票證，但是只能在下表顯示的安全性組態中。  
  
|安全性模式|傳輸用戶端認證類型|[憑證]|  
|-------------------|--------------------------------------|------------------------------------|  
|傳輸|Basic|不適用|  
|傳輸|Digest|不適用|  
|傳輸|Ntlm|不適用|  
|傳輸|Windows|不適用|  
|傳輸|憑證|不適用|  
|訊息|不適用|UserName|  
|訊息|不適用|Windows|  
|訊息|不適用|憑證|  
|TransportWithMessageCredential|不適用|Windows|  
|TransportWithMessageCredential|不適用|憑證|  
|TransportWithMessageCredential|不適用|UserName|  
  
 **單一登入 」 支援的 Wcf-nettcp 接收位置**  
  
 WCF-NetTcp 接收配接器只能在下表顯示的安全性組態中，從 SSO 伺服器發行 SSO 票證。  
  
|安全性模式|傳輸用戶端認證類型|[憑證]|  
|-------------------|--------------------------------------|------------------------------------|  
|傳輸|Windows|不適用|  
|傳輸|憑證|不適用|  
|訊息|不適用|憑證|  
|訊息|不適用|Windows|  
|訊息|不適用|UserName|  
|TransportWithMessageCredential|不適用|憑證|  
|TransportWithMessageCredential|不適用|Windows|  
|TransportWithMessageCredential|不適用|UserName|  
  
 S**單一登入支援 Wcf-netnamedpipe 接收位置**  
  
 WCF-NetNamedPipe 接收配接器只能在下表顯示的安全性組態中，從 SSO 伺服器發行 SSO 票證。  
  
|安全性模式|傳輸用戶端認證類型|[憑證]|  
|-------------------|--------------------------------------|------------------------------------|  
|傳輸|不適用|不適用|  
  
 **單一登入 」 支援 Wcf-custom 和 Wcf-customisolated 接收位置**  
  
 對於要發出 SSO 票證的 WCF-Custom 和 WCF-CustomIsolated 接收位置，接收位置所使用的安全性設定會要求 WCF 用戶端傳送可由 Windows Communication Foundation 模擬的認證。 WCF 支援模擬各種類型的用戶端認證。 WCF 支援進行模擬的認證類型的詳細資訊，請參閱 < 委派和模擬與 WCF >，網址[http://go.microsoft.com/fwlink/?LinkId=87476](http://go.microsoft.com/fwlink/?LinkId=87476)。  
  
## <a name="single-sign-on-support-for-the-wcf-send-ports"></a>WCF 傳送埠的單一登入支援  
 對於 WCF 傳送埠，您可以在下表所示的安全性組態中，指定只供 SSO 使用的分支機構應用程式名稱。  
  
|安全性模式|傳輸用戶端認證類型|[憑證]|  
|-------------------|--------------------------------------|------------------------------------|  
|傳輸|Digest|不適用|  
|傳輸|Basic|不適用|  
|訊息|不適用|UserName|  
  
> [!NOTE]
>  WCF 傳送埠，以驗證及贖回 SSO 票證正常運作， **SSOTicket**和**OriginatorSID**內容屬性中必須有要傳送的訊息。 已啟用「單一登入」的接收位置可以從傳送者的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 帳戶升級這些屬性。  
  
## <a name="see-also"></a>另請參閱  
 [企業單一登入](../core/enterprise-single-sign-on2.md)