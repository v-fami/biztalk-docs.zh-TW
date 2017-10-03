---
title: "HTTP 配接器安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, HTTP adapters
- configuring [HTTP adapters], security
- HTTP adapters, security
ms.assetid: ef6043c2-c62a-40e5-b2e1-53e60f87a761
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb4e5909a61040a2bcd2dd84a81f81077d25a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-security-recommendations"></a>HTTP 配接器安全性建議
您可以使用 HTTP 配接器透過「超文字傳輸通訊協定」(HTTP) 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與應用程式之間交換資訊。 應用程式可以藉由傳送 HTTP POST 或 HTTP GET 要求到指定的 HTTP URL 來傳送訊息到伺服器。 如需 HTTP 配接器的詳細資訊，請參閱[HTTP 配接器](../core/http-adapter.md)。 建議您使用下列指導方針在環境中部署 HTTP 配接器並保護其安全：  
  
-   請確定您為 HTTP 配接器設定 Internet Information Services (IIS) 設定。 如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
-   若您使用 7.0，請確定您遵循 IIS 7.0 中對於設定應用程式隔離的建議。  
  
-   當您使用基本驗證，或當您未使用訊息層級加密，建議使用安全通訊端層 (SSL) 來接收和傳送訊息，以確保未經授權的人員無法找出的使用者認證。  
  
-   建議您使用 Windows 整合式驗證來傳送和接收訊息。  
  
-   建議您不要重新命名、複製或移動 ISAPI 延伸模組檔案。 這可確保安全性更新安裝程式可以正確地套用任何與此檔案相關的可能安全性更新。  
  
-   您應該為包含 ISAPI 延伸模組檔案的目錄以及為接收訊息所建立的虛擬目錄，使用強式判別存取控制清單 (DACL)。 執行 HTTP 配接器之主控件的「BizTalk 外掛式主控件」群組成員需要讀取和執行權限，而 HTTP 配接器所驗證的使用者則需要這些目錄的讀取權限。  
  
-   當您搭配 HTTP 傳送配接器使用 SSL 用戶端憑證時，必須手動設定這些憑證。  
  
-   如同其他的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件，建議您不要將 HTTP 配接器放置在周邊網路中。 若您這麼做，就必須開啟從周邊網路到資料網域的連接埠，以便 SQL Server 傳輸至 MessageBox 資料庫，這樣非常容易有風險。 建議您在處理網域中 (也就是說，不要在周邊網路中) 設定 HTTP 配接器。 接著，您就可以設定最外層的防火牆 (FW4)，以透過處理網域中的防火牆 (FW3) 來轉送 HTTP 要求。 在此情況下，您不需要周邊網路中的 IIS。 此機制稱為反向 Proxy。 (Forefront Threat Management Gateway (TMG) 2010 Server 實作稱為「Web 發佈」。)  
  
-   當您為 HTTP 接收位置建立應用程式集區時，必須將它設定為在下列帳戶下執行：屬於執行 HTTP 接收配接器的外掛式主控件之 Windows 群組以及 Internet Information Services 工作處理序群組的成員 (IIS_WPG group)。 接著，您就必須使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 來設定 HTTP 接收配接器的主控件執行個體，才能使用此帳戶。 若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。 如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)