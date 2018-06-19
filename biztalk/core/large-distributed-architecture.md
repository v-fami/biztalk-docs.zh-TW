---
title: Large Distributed Architecture |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- data, domains
- corporate domains
- networks
- domain types, service
- domain types, processing
- screened subnet
- service domains
- domain types, corporate
- domain types, data
- perimeter networks
- processing domains
- demilitarized zone
- architecture, large distributions
ms.assetid: 3cfc07c4-0b1d-489b-9a29-55187fde0539
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c29bda1c60b59db42fabacaa0c02175aed90bda
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264790"
---
# <a name="large-distributed-architecture"></a>大型分散式架構
如需系統架構的完整資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 本節所呈現的架構是用於生產環境。 並不包含開發或測試環境，也不適合當做環境中網路管理的建議。 執行您的設定從開發進入測試環境中，並從測試進入生產環境的相關的詳細資訊，請參閱[部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)。  
  
 下圖顯示考量到深層防禦的高度分散式 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構。  
  
 ![Large Distributed Architecture](../core/media/06c5ae00-17aa-42f5-88d1-487bf7720183.gif "06c5ae00-17aa-42f5-88d1-487bf7720183")  
分散式 BizTalk Server 安全架構  
  
 此架構包含下列五個網域：  
  
 **周邊網路。** 周邊網路 （也稱為 DMZ 和遮蔽式子網路） 時，包含提供網際網路相關服務之企業的伺服器。 此網域可以包含的伺服器主要的網際網路對向傳輸傳送和接收訊息的實體位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在此網域中沒有 BizTalk Server、BizTalk 接收位置或企業單一登入伺服器。 若您使用 SOAP 或 HTTP 配接器，則可以使用反向 Proxy 規則 (Forefront Threat Management Gateway (TMG) 2010 Server 實作稱為「Web 發佈」) 從外部式網際網路的防火牆 (FW4) 傳遞訊息到保護服務介面網域 (FW3) 的防火牆。 如需 Web 發佈 」 規則的詳細資訊，請參閱 Microsoft 網站，網址[http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340)。  
  
 上圖中，在周邊網路中的伺服器會代表在外部網域的伺服器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 因此，其中一些伺服器可能在遠端位置。 例如，檔案傳輸通訊協定 (FTP) 伺服器可以在遠端位置；Simple Mail Transfer Protocol (SMTP) 伺服器可以是企業的電子郵件伺服器、網際網路服務提供者 (ISP) 伺服器或遠端 SMTP 伺服器。  
  
 **服務介面網域。** 這是開始訊息處理的網域。 此網域包含具有 BizTalk 接收與傳送處理常式的伺服器。 這是 where[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]連接埠，接收位置、 管線、 對應、 結構描述和組件的位置來接收、 路由和傳送訊息。 此網域中的 BizTalk Server 數目依企業效能需求所需的主控件與主控件執行個體的數目而定。  
  
 **服務網域。** 此網域包含服務介面網域中的伺服器所信任、而且成功處理訊息時所需的服務，但是這需要較高層級的防禦以免遭受來自周邊網路 (例如具有 BizTalk 協調流程、管線、「企業單一登入」(SSO) 服務、商務規則引擎以及其他商務程序的處理伺服器) 的攻擊。  
  
 此網域還包含企業網域需要存取但仍需要保護以免於外部威脅的服務。 這個網域中伺服器的其中一個裝載管理工具： BizTalk 管理主控台 」 和 「 企業單一登入 (SSO) 管理公用程式。 此網域還包含 SSO 主要密碼伺服器，其中保存 SSO 系統用來加密 SSO 資料庫中資料的主要密碼 (加密金鑰)。 其中一個伺服器，在這個網域中有支援追蹤狀況監控與商務監控資料的主控件的主控件執行個體。  
  
> [!NOTE]
>  在「企業單一登入」系統中，有些處理伺服器可能只包含無 BizTalk Server 元件的 SSO 服務。 如需詳細資訊，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。  
  
 **資料網域。** 它包含 SQL Server 資料庫儲存重要的商務和處理資料，以及不信任任何其他網域最遠網際網路資料網域。 雖然您可以讓每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫的不同伺服器上執行 SQL Server，建議合併它們執行的主要類型為基礎的資料庫 （大部分是讀取作業，最常寫入的作業，或兩者）：  
  
-   每個 MessageBox 資料庫的 SQL Server。 您可以新增多個 MessageBox 資料庫使負載平衡。 這些是密集讀取與密集寫入的資料庫。  
  
-   SSO 資料庫的 SQL Server。 BizTalk Server 大部分是讀取此資料庫中的作業。 此資料庫保存敏感性資料，需要最嚴格的存取權限。  
  
-   BizTalk 管理 」 和 「 商務規則引擎資料庫的 SQL Server。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]大部分是讀取這些資料庫中的作業。 此伺服器也包含追蹤資料庫，這是密集寫入的資料庫。  
  
-   「分析伺服器追蹤」資料庫的 SQL Server。  
  
-   Microsoft Operations Manager (MOM) 資料庫的 SQL Server。  
  
-   供記錄傳送之用的目的地系統之 SQL Server  
  
> [!IMPORTANT]
>  容錯移轉保護，我們建議您叢集每個 BizTalk 資料庫。 如需有關 SQL Server 容錯移轉叢集的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016)。  
  
> [!NOTE]
>  如需記錄傳送的目的系統的詳細資訊，請參閱[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。  
  
 在上圖中，Forefront Threat Management Gateway (TMG) 2010 Server 扮演軟體防火牆的角色，以保護和圈管其中每個網域。 此外，每個網域都有它自己的網域控制站，建立從包含重要伺服器 (資料網域) 的網域到面對外部伺服器 (周邊網路與企業網域) 的信任，而且伺服器只能存取需要連線的其他網域中的服務。 有一個限制從服務介面與服務網域 (FW1) 到資料網域之流量的防火牆。 同理，也有一個限制從服務介面與作業網域到服務網域之流量的防火牆 (FW2)。  
  
 **公司網域。** 這是內部網路網域，其中包含企業或部門中所有的桌上型電腦，以及提供公司內資訊工作者服務的所有伺服器。 此網域中有兩個不同的邏輯容器：  
  
-   **內部網路服務。** 此容器擁有接收和傳送訊息的內部夥伴 SQL 和檔案配接器的伺服器。 雖然這是內部網路，但它不同於多數使用者都擁有帳戶與服務的內部網路。 與圖中的周邊網路類似，此容器中有些伺服器可以在不同的位置。 例如，FILE 配接器的傳送和接收位置 (資料夾) 可以在服務介面網域外部的任一層，而您可以將為 SQL 配接器執行 SQL Server 的伺服器放在服務介面網域上。  
  
-   **作業。** 此容器擁有 IT 專家用來遠端管理、維護以及監控環境中所有伺服器效能與狀況的「終端服務」用戶端。 IT 專家可以使用「終端服務」連線到服務網域的管理伺服器，然後在管理伺服器上執行環境中所有伺服器的管理工作。  
  
 您的企業網域中可能會有開發電腦，但這些電腦的組態不在本文的討論範圍中。  
  
 如需 BizTalk Server 架構，包括資訊工作者服務的詳細資訊，請參閱[具有資訊工作者服務的大型分散式架構](../core/large-distributed-architecture-with-information-worker-services.md)。  
  
 網域之間的信任如下：  
  
-   資料網域不信任任何其他網域。  
  
-   服務介面網域信任資料網域。  
  
-   服務網域信任資料網域。  
  
-   企業網域信任服務網域。  
  
 如需有關如何設定網域和信任的防火牆的詳細資訊，請參閱 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230)。  
  
 前面的圖例著重在安全性，而您也可以擴充「網路負載平衡」(NLB) 和叢集服務的架構以提升可用性和效能。  
  
 如需有關高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
 如需有關效能的詳細資訊，請參閱[規劃維持效能](../core/planning-for-sustained-performance.md)。  
  
 下表摘要您可根據需要取得的「服務等級協議」(SLA)，以「網路負載平衡」(NLB) 設定的伺服器類型：  
  
|名稱|類型|網域|  
|----------|----------|------------|  
|HTTP (Rec)|Internet Information Services|周邊網路|  
|接收處理常式 (外掛式)|Internet Information Services|服務介面網域|  
|BAM 入口網站|Internet Information Services|服務介面網域|  
  
 下表摘要您可根據需要取得的「服務等級協議」(SLA) 以進行叢集的伺服器類型：  
  
|名稱|類型|網域|  
|----------|----------|------------|  
|Exchange (傳送)|Exchange Server|周邊網路|  
|FTP 與 POP3 配接器的接收處理常式 (內含式主控件)|BizTalk Server|服務介面網域<br /><br /> 企業網域|  
|主要密碼伺服器|BizTalk Server|服務網域|  
|所有 SQL Server|SQL Server|資料網域|  
  
 如需 BizTalk Server 架構，包括資訊工作者服務的詳細資訊，請參閱[具有資訊工作者服務的大型分散式架構](../core/large-distributed-architecture-with-information-worker-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)   
 [縮小架構](../core/scaled-down-architecture.md)