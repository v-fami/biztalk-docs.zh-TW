---
title: "SOAP 配接器安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, security
- security, SOAP adapters
ms.assetid: f869bd82-df93-45e1-b747-b538820253fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3053bccde7830d2e8275c8e2f6f668c428709860
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-security-recommendations"></a>SOAP 配接器安全性建議
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用 SOAP 配接器來發佈 (接收) 和取用 (傳送) Web 服務。 如需有關 SOAP 配接器的詳細資訊，請參閱[SOAP 配接器](../core/soap-adapter.md)。 如需 Web 服務的詳細資訊，請參閱[使用 Web Services](../core/using-web-services.md)。 建議您依照這些指導方針，來保護和部署您作業環境中的 SOAP 配接器。  
  
-   如需發佈 Web 服務的安全性建議，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
-   SOAP 配接器會利用超文字傳輸通訊協定 (HTTP)，從 BizTalk Server 傳送和接收訊息。 因此，您必須遵循安全性建議來保護 Internet Information Services (IIS) 的安全。 若您使用 IIS 7.0，請確定您遵循 IIS 7.0 中對於設定應用程式隔離的建議。 如需詳細資訊，請參閱[建立應用程式集區 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=196674)。  
  
-   當您為 SOAP 接收位置建立應用程式集區時，必須將它設定成在下列帳戶下執行：屬於執行 SOAP 接收配接器之外掛式主控件的 Windows 群組及 Internet Information Services 工作處理序群組 (IIS_WPG group) 的成員。 接著您必須設定 SOAP 接收配接器的主控件執行個體，才能使用此帳戶。 若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。  
  
-   當您利用 SOAP 傳送配接器來使用「安全通訊端層」(SSL) 用戶端憑證時，必須手動設定這些憑證。  
  
-   在取用 Web 服務時，您可以使用匿名、基本、摘要、Windows 整合或是用戶端憑證來驗證。 使用基本驗證來取用 Web 服務時，建議您使用 SSL，以確保未授權的人員無法從訊息讀取使用者認證。  
  
-   您可以在需要將前端使用者的內容對應到後端系統之認證的實例中，使用「企業單一登入」(SSO)。 如需詳細資訊，請參閱[如何對應單一登入認證](../core/how-to-map-single-sign-on-credentials.md)。  
  
-   當您使用基本驗證時，或當您未在訊息層次使用加密時，建議您使用 SSL 來接收和傳送訊息，以確保未經授權的人員無法讀取使用者認證。  
  
-   建議您使用 Windows 整合式驗證來傳送和接收訊息。  
  
-   執行 SOAP 配接器的電腦也有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段。 建議您不要在週邊網路中放置 SOAP 配接器。 若您這麼做，就必須從 SQL Server 資料網域的週邊網路開啟連接埠，以連至 MessageBox 資料庫，但這樣將會使 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段暴露在可能的攻擊之下。 建議您在處理網域中 (也就是說，不要在週邊網路中) 設定 SOAP 配接器。 接著就可以設定最外層的防火牆，以透過處理網域中的防火牆來轉送 SOAP 要求。 此機制稱為反向 Proxy。 (Forefront Threat Management Gateway (TMG) 2010 Server 實作稱為「Web 發佈」。)  
  
## <a name="see-also"></a>另請參閱  
 [接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)