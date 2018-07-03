---
title: WCF 配接器安全性建議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF adapters, security
- security, WCF adapters
ms.assetid: bbaaca56-9ad5-4122-a8e9-6e975d308230
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f871c68277c487efcc7400a3ae54db749090148e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993447"
---
# <a name="wcf-adapters-security-recommendations"></a>WCF 配接器安全性建議
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用 WCF 配接器來發佈 (接收) 和使用 (傳送) WCF 服務。 建議您依照這些指導方針來保護和部署您作業環境中的 WCF 配接器。  
  
 如需有關 WCF 配接器的詳細資訊，請參閱 < [WCF 配接器](../core/wcf-adapters.md)。 如需有關 WCF 服務的詳細資訊，請參閱 <<c0> [ 使用 WCF 服務](../core/using-wcf-services.md)s。  
  
## <a name="security-recommendations-for-all-wcf-adapters"></a>針對所有 WCF 配接器的安全性建議  
  
-   您可以在需要將前端使用者的內容對應到後端系統之認證的實例中，使用「企業單一登入」(SSO)。  
  
-   並非所有的服務都必須發佈中繼資料。 停用中繼資料發佈功能，可減少服務的攻擊面並降低無意間洩漏資訊的風險。 中繼資料的相關安全性問題的詳細資訊，請參閱 < 安全性考量與中繼資料 >，網址[ http://go.microsoft.com/fwlink/?LinkId=196671 ](http://go.microsoft.com/fwlink/?LinkId=196671)。  
  
-   並非所有中繼資料端點繫結和服務端點繫結的組合都有效。 在某些狀況下，中繼資料端點的繫結組態必須與其服務端點的繫結組態一致。 例如，提供中繼資料的位置與接收位置相同時，如果接收位置使用依賴 HTTPS 的安全性模式，則中繼資料端點便無法設定為使用要求 HTTP 傳輸的安全性模式。  
  
    > [!NOTE]
    >  透過使用相同位置但所需的安全性模式依賴 HTTPS 傳輸，「 BizTalk WCF 發佈精靈 」 產生時，Web.config 檔案中的服務端點的 HTTP 傳輸發佈中繼資料時您必須設定這兩個**httpsGetEnabled**並**httpGetEnabled**屬性**true**。  
  
-   WCF 配接器會運用 Windows Communication Foundation (WCF) 的安全性功能來通訊。 因此，瞭解 WCF 安全性功能和限制很重要。 WCF 的安全性功能的相關詳細資訊，請參閱 < Windows Communication Foundation 安全性 >，網址[ http://go.microsoft.com/fwlink/?LinkId=87806 ](http://go.microsoft.com/fwlink/?LinkId=87806)。  
  
## <a name="security-recommendations-for-the-isolated-wcf-adapters"></a>外掛式 WCF 配接器的安全性建議  
  
- 如需發佈 Web 服務的安全性建議，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
- 外掛式 WCF 配接器 (例如 WCF-CustomIsolated、WCF-BasicHttp 和 WCF-WSHttp 配接器) 會利用「超文字傳輸通訊協定」(HTTP)，將訊息傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並從中接收訊息。 因此，您必須遵循安全性建議來保護 Internet Information Services (IIS) 的安全。  
  
- 當您為外掛式 WCF 接收位置建立應用程式集區時，必須將它設定為在下列帳戶下執行：屬於執行 WCF 接收配接器的外掛式主控件之 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 群組以及「Internet Information Services 工作者處理序」群組 (IIS_WPG 群組) 的成員。 接著您必須設定 WCF 接收配接器的主控件執行個體，才能使用此帳戶。 若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。  
  
## <a name="security-recommendations-for-the-wcf-custom-adapter"></a>WCF-Custom 配接器的安全性建議  
  
-   如果 Wcf-custom 接收位置使用 HTTP 核心模式驅動程式 (HTTP.sys)，例如**httpsTransport** Secure Sockets Layer (SSL) 通訊，接收位置的繫結項目必須有憑證針對每個通訊端 （IP 位址/連接埠組合） 登錄。 請使用 HttpCfg.exe 工具將 SSL 憑證繫結到電腦上的連接埠。 詳細資訊，請參閱 「 如何以:: 設定連接埠使用 SSL 憑證 」，網址[ http://go.microsoft.com/fwlink/?LinkId=86384 ](http://go.microsoft.com/fwlink/?LinkId=86384)。  
  
## <a name="security-recommendations-for-the-wcf-netmsmq-adapter"></a>WCF-NetMsmq 配接器的安全性建議  
  
-   若要使用 Wcf-netmsmq 配接器，您必須針對相同的方式設定 Wcf-netmsmq 配接器的 MSMQ 安全性設定[netMsmqBinding](http://go.microsoft.com/fwlink/?LinkId=87813)。 如需有關如何設定 MSMQ 安全性設定**netMsmqBinding**，請參閱 < 佇列訊息疑難排解"」，網址[ http://go.microsoft.com/fwlink/?LinkId=87816 ](http://go.microsoft.com/fwlink/?LinkId=87816)。  
  
## <a name="wcf-adapters-use-the-chaintrust-mode-to-validate-certificates"></a>WCF 配接器會使用 ChainTrust 模式來驗證憑證  
  
-   因為標準的 WCF 接收配接器使用，所以[ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960)模式來驗證用戶端和服務的憑證，您必須安裝 CA 憑證鏈結來驗證 X.509 憑證。 您可以使用 WCF-Custom 或 WCF-CustomIsolated 配接器變更此預設行為。  
  
## <a name="security-auditing-for-the-wcf-adapters"></a>WCF 配接器的安全性稽核  
  
- WCF 配接器預設不會使用 WCF 安全性稽核功能。 有幾個方式可啟用 WCF 配接器的 WCF 安全性稽核功能。 WCF 安全性稽核功能的詳細資訊，請參閱 < 稽核安全性事件 >，網址[ http://go.microsoft.com/fwlink/?LinkId=88975 ](http://go.microsoft.com/fwlink/?LinkId=88975)。  
  
- 若要使用 WCF 安全性稽核使用 Wcf-custom 接收配接器的功能，您可以設定**ServiceSecurityAuditBehavior**接收位置。  
  
- 對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。 對於外掛式 WCF 配接器，您可以修改 Web.config 檔案 (「BizTalk WCF 服務發佈精靈」在 Web 應用程式資料夾中建立的檔案) 來啟用 WCF 追蹤。 若要修改 BTSNtSvc.exe.config 或 Web.config，請開啟組態檔並設定 WCF 追蹤，如以下組態範例所示：  
  
  > [!NOTE]
  >  BTSNTSvc.exe.config 永遠與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  > 
  > [!NOTE]
  >  修改 BTSNTSvc.exe.config 檔案後，您必須重新啟動執行內含式 WCF 接收位置的主控件執行個體。  
  
  ```  
  <configuration>  
      <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="ServiceBehaviorConfiguration">  
              <serviceSecurityAudit  
                        auditLogLocation="Application"  
                        suppressAuditFailure="true"  
                        serviceAuthorizationAuditLevel="SuccessOrFailure"  
  messageAuthenticationAuditLevel="SuccessOrFailure" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
        <services>  
          <service name="Microsoft.BizTalk.Adapter.Wcf.Runtime.BizTalkServiceInstance" behaviorConfiguration="ServiceBehaviorConfiguration">  
          </service>  
        </services>        
      </system.serviceModel>  
  </configuration>  
  ```  
  
- 您也可以使用與安全性有關的效能計數器 (例如 Security Calls Not Authorized) 來監視 WCF 配接器。 如需如何啟用 WCF 效能計數器的詳細資訊，請參閱[WCF 配接器效能計數器](../core/wcf-adapters-performance-counters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安全性規劃](../core/planning-for-security.md)