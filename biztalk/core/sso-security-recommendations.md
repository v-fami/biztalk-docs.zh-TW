---
title: SSO 安全性建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- Kerberos protocol, SSO
- deploying, SSO
- user accounts, SSO
- deploying, security
- SQL Server, SSO
- security, SSO
- SSO, Kerberos protocol
- SSO, auditing
- best practices, deploying
- SSO, Windows groups
- SSO, best practices
- SSO, perimeter network
- Windows groups, SSO
- SSO, SQL Server access
- best practices, security
- Master Secret server, clustering
- perimeter networks
- auditing [SSO]
- SSO, security
- SSO, user accounts
- Master Secret server, best practices
ms.assetid: 7ae922b4-fd48-41f4-aaab-419a5e22c753
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a86e669e603eaabf142ce446b8d7204a6cc0091
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279838"
---
# <a name="sso-security-recommendations"></a>SSO 安全性建議
使用「企業單一登入」(SSO) 系統，使用者只需使用一組認證，便可連接至不同的系統。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用 SSO 系統做為機密資訊的存放區。 安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段時會自動安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，不過，您也可在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以外的環境，將「企業單一登入」以獨立元件方式安裝。 如需企業單一登入的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。 建議您遵循以下指導方針，在您的環境中保護和部署「企業單一登入」(SSO) 服務和資源。  
  
## <a name="general-deployment-recommendations-for-sso"></a>SSO 的一般部署建議  
  
-   即使您的環境中有多個 BizTalk 群組，但整個環境中必須只能有一個主要密碼伺服器和一個 SSO 資料庫。 在設定其他的 BizTalk 和 SSO 伺服器之前，必須先設定這兩個伺服器。  
  
-   您的環境必須要有一個時間伺服器，以確保所有 SSO 伺服器均同步。 若 SSO 伺服器的時鐘未同步，環境的安全性會受到影響。  
  
-   假設整個環境中只有一個主要密碼伺服器，建議主要密碼伺服器使用主動-被動叢集組態。 如需叢集化主要密碼伺服器的詳細資訊，請參閱[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。  
  
-   主要密碼伺服器保存 SSO 系統在 SSO 資料庫中用來加密資訊的加密金鑰。 建議您不要在此電腦安裝或設定任何其他產品或服務。  
  
    > [!NOTE]
    >  您安裝和設定主要密碼伺服器的電腦，不一定要是伺服器。  
  
-   主要密碼伺服器應能存取卸除式媒體或 NTFS 檔案系統資料夾，才能備份和還原主要密碼。 若您使用卸除式媒體，請確定使用適當措施以保護卸除式媒體。 若將主要密碼備份至 NTFS 檔案系統，請保護檔案和資料夾的安全性。 只有 SSO 系統管理員才可存取此檔案。  
  
-   您應在主要密碼伺服器產生主要密碼後，立即將它備份。 這樣在主要密碼伺服器故障時，才能夠還原 SSO 資料庫中的資料。 如需備份主要密碼的詳細資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。  
  
-   備份目前的密碼，或定期產生新密碼，例如 1 個月 1 次。 沒有密碼，便無法從 SSO 資料庫中擷取資訊。 如需有關備份和還原主要密碼的詳細資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。  
  
## <a name="security-recommendations-for-sso-groups-and-accounts"></a>SSO 群組和帳戶的安全性建議  
  
-   建議使用 Windows 群組而非單一使用者帳戶，特別是「SSO 系統管理員」和「SSO 分支機構系統管理員」群組。 這些群組至少需有兩個使用者帳戶，以做為群組的成員。  
  
-   SSO 執行階段服務帳戶和 SSO 系統管理員使用者帳戶應該是不同的帳戶，即使它們是同一個「SSO 系統管理員」群組的成員。 執行管理工作 (例如產生和備份密碼) 的 SSO 系統管理員使用者必須是 Windows 管理員，而 SSO 執行階段服務帳戶則不一定要是 Windows 管理員。  
  
    > [!IMPORTANT]
    >  Windows 管理員使用者權限不能取代 SSO 系統管理員使用者權限。 即使您已是 Windows 管理員，但仍需為 SSO 系統管理員群組的成員，才能執行任何 SSO 管理層級工作。  
  
-   若使用 SSO 票證功能，必須使用處理網域 (SSO 伺服器所在的網域) 的電腦所識別的網域帳戶。  
  
-   建議主要密碼伺服器所對應的 SSO 服務，使用專用的服務帳戶。  
  
-   SSO 系統管理員帳戶是 SSO 系統中高度授權的帳戶，也是擁有 SSO 資料庫的 SQL Server 管理員帳戶。 您應該具備 SSO 系統管理員的專用帳戶，而且不得將這些帳戶用於任何其他用途。 您應將 SSO 系統管理員群組的成員資格，限制為負責執行和維護 SSO 系統的帳戶。  
  
-   您必須手動將 BizTalk 系統管理員群組新增至「SSO 分支機構系統管理員」群組，如此 BizTalk 系統管理員便能使用 SSO 系統，將配接器的組態資訊儲存在 SSO 資料庫中。 只有管理配接器的 BizTalk 系統管理員需為「SSO 分支機構系統管理員」群組的成員， BizTalk 系統管理員不需為 SSO 系統管理員。  
  
## <a name="security-recommendations-for-an-sso-deployment"></a>SSO 部署的安全性建議  
  
-   若您的網路支援 Kerberos 驗證，您應該註冊所有 SSO 伺服器。 當您在主要密碼伺服器與 SSO 資料庫之間使用 Kerberos 驗證時，需在 SSO 資料庫所在的 SQL Server 上設定服務主要名稱 (SPN)。 如需設定 「 服務主體名稱的詳細資訊，請參閱 Microsoft 下載網站[http://go.microsoft.com/fwlink/?LinkId=195797](http://go.microsoft.com/fwlink/?LinkId=195797)。  
  
-   當執行[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，如果主要密碼伺服器位於不同的網域從其他 SSO 伺服器和 SSO 資料庫中，您必須停用 RPC 安全性 （用於電腦之間的 Data Transaction Coordinator (DTC) 驗證) 主要密碼伺服器、 （處理在處理網域中的電腦） 的 SSO 伺服器和 SSO 資料庫。 RPC 安全性是 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 與 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 中的 DTC 功能。 當您停用 RPC 安全性時，RPC 呼叫的 DTC 驗證安全性等級會回到 Microsoft Windows Server 2003 中提供。  
  
-   SSO 系統管理員應定期監控主要密碼伺服器和 SSO 伺服器中的事件日誌，以瞭解 SSO 稽核事件。  
  
-   除了防火牆，建議在 SSO 伺服器和 SSO 資料庫之間使用網際網路通訊協定安全性 (IPSec) 或安全通訊端層 (SSL)。 如需有關 SSL 的詳細資訊，請參閱 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=195798](http://go.microsoft.com/fwlink/?LinkId=195798)。 如需有關所有 SSO 伺服器與 SSO 資料庫之間使用 SSL 的詳細資訊，請參閱[如何針對 SSO 啟用 SSL](../core/how-to-enable-ssl-for-sso.md)。  
  
## <a name="perimeter-network"></a>周邊網路  
 執行 Internet Information Services (IIS) 和「企業單一登入」時，請按照以下建議執行：  
  
-   若 IIS 是在周邊網路 (也稱為非軍事區域、DMZ 以及過濾的子網路)，請在防火牆後面提供另一個 IIS 伺服器來連接 SSO 系統。  
  
-   請不要開啟 IIS 上的遠端程序呼叫 (RPC) 連接埠。  
  
## <a name="sql-server-access"></a>SQL Server 存取  
 所有 SSO 伺服器都會存取 SQL Server SSO 資料庫。 如需如何保護 SQL Server 資料庫的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=33175](http://go.microsoft.com/fwlink/?LinkId=33175)。  
  
 建議您使用安全通訊端層 (SSL) 和 (或) 網際網路通訊協定安全性 (IPSec)，以保護 SSO 伺服器和 SSO 資料庫之間資料傳輸的安全性。 如需有關使用 SSL 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=195798](http://go.microsoft.com/fwlink/?LinkId=195798)。  
  
 若只想針對 SSO 伺服器和 SSO 資料庫之間的連線啟用 SSL，您可使用 ssoconfig 公用程式在每個 SSO 伺服器上設定 SSL 支援。 此選項可讓 SSO 永遠使用 SSL 來存取 SSO 資料庫。 如需詳細資訊，請參閱[如何針對 SSO 啟用 SSL](../core/how-to-enable-ssl-for-sso.md)。  
  
## <a name="strong-passwords"></a>增強式密碼  
 對於所有帳戶而言，使用強式密碼十分重要，特別是「SSO 系統管理員」群組成員的帳戶，因為這些使用者可以控制整個 SSO 系統。  
  
## <a name="sso-administrator-accounts"></a>SSO 系統管理員帳戶  
 建議您針對在不同電腦上執行的 SSO 服務，使用不同的服務帳戶。 您不應使用執行管理作業 (例如產生和備份 SSO 服務的密碼) 的 SSO 系統管理員帳戶。 SSO 服務帳戶不應是該電腦的本機系統管理員，但執行管理作業的 SSO 系統管理員必須是電腦的本機系統管理員，才能執行部分作業。  
  
## <a name="master-secret-server"></a>主要密碼伺服器  
 強烈建議您保護和鎖定主要密碼伺服器。 您不應將此伺服器當成處理伺服器。 此伺服器的唯一用途應該是保存主要密碼。 您應確定此電腦的實體安全性，且只有「SSO 系統管理員」才能存取此電腦。  
  
## <a name="kerberos"></a>Kerberos  
 SSO 支援 Kerberos，且建議您為 SSO 設定 Kerberos。 要在 SSO 設定 Kerberos，必須註冊 SSO 服務的 Secure Principal Name (SPN)。 依照預設，當您設定 Kerberos 時，SSO 會使用該 SPN 來驗證使用 SSO 服務的元件。 建議您在 SSO 管理子服務和 SSO 伺服器之間設定 Kerberos 驗證。 您也可以在 SSO 伺服器之間、SSO 伺服器之間，以及 SSO 資料庫所在的 SQL Server 之間使用 Kerberos 驗證。  
  
 要設定和驗證 Kerberos，您可使用公用程式 setspn 和 kerbtray。 如需有關這些公用程式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178)。  
  
## <a name="delegation"></a>委派  
 使用 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 時可使用限制委派，但建議您不要使用委派來執行「單一登入系統管理員」的工作。 同樣地，建議您不要將其他工作或使用者權限委派給「單一登入」系統管理員。  
  
## <a name="auditing"></a>稽核  
 稽核是追蹤環境資訊的重要機制。 「企業單一登入」(SSO) 會稽核所有在 SSO 資料庫執行的作業。 SSO 使用資料庫本身的事件日誌和稽核日誌。 SSO 為「單一登入」伺服器提供兩種稽核層級：  
  
-   正面稽核層級會稽核成功的作業  
  
-   負面稽核層級會稽核失敗的作業  
  
 SSO 系統管理員可設定符合公司政策的正面和負面稽核層級。  
  
 您可以在下列層級的其中一個設定正面和負面稽核：  
  
 0 = 無。 此層級不會發出稽核訊息  
  
 1 = 低  
  
 2 = 中  
  
 3 = 高。 此層級會儘可能發出最多的稽核訊息  
  
 正面稽核的預設值為 0 （無）、 和負面稽核的預設值為 1 （低）。 您可按照 SSO 系統的稽核層級來變更這些值。  
  
> [!IMPORTANT]
>  「企業單一登入」稽核會發出「單一登入」服務產生的訊息。 這不是安全性稽核，且 SSO 系統不會將資訊儲存在「事件日誌」的安全記錄檔中。 SSO 系統會將 SSO 稽核訊息直接儲存至「應用程式事件日誌」。  
  
### <a name="database-level-auditing"></a>資料庫層級稽核  
 若是資料庫層級稽核，SSO 系統會將所有在 SSO 資料庫執行的作業，記錄至資料庫的稽核表格。 這些稽核表格的大小定義在 SSO 系統層級。 您可以稽核刪除的分支機構應用程式、刪除的對應，以及所執行的認證查詢。 依照預設，稽核大小設定為 1,000 個項目。 SSO 系統管理員可變更此大小，以符合公司的政策。  
  
## <a name="using-sso-accounts"></a>使用 SSO 帳戶  
 本節包含在「企業單一登入」(SSO) 系統中使用網域、本機群組以及個別帳戶的最佳作法。  
  
### <a name="domain-windows-groups-and-accounts"></a>網域 Windows 群組和帳戶  
 使用網域 Windows 群組時，適用以下建議：  
  
-   使用網域群組和網域帳戶。  
  
-   當使用[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]ENTSSO 服務帳戶可以設定為在 Network Service 帳戶下執行。 但是，基於安全性理由不建議這樣做，因為必須授與網路服務帳戶 SSO 系統管理員權限。 建議您為 ENTSSO 服務帳戶使用唯一的網域服務帳戶作為替代。  
  
-   對於 SSO 系統管理員，請使用網域群組。 您不應將個人網域帳戶指定為 SSO 系統管理員，因為您無法將此帳戶變更為另一個個人帳戶。  
  
-   您可將個別網域帳戶指定為 SSO 分支機構系統管理員，但建議您使用網域群組。  
  
-   您可將個別網域帳戶指定為應用程式系統管理員，但建議您使用網域群組。  
  
-   應用程式使用者帳戶必須使用網域群組。 SSO 應用程式使用者帳戶不支援個別帳戶。  
  
-   這些 SSO 存取帳戶可指定多個帳戶。  
  
## <a name="see-also"></a>另請參閱  
 [企業單一登入伺服器的連接埠](../core/ports-for-the-enterprise-single-sign-on-servers.md)   
 [最小安全性使用者權限](../core/minimum-security-user-rights.md)