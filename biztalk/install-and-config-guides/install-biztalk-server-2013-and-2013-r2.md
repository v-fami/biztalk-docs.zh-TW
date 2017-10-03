---
title: "安裝 BizTalk Server 2013 和 2013 R2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4665ea-6f2c-477f-98ec-1cebef05ad4a
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3563fe263a3921979c7a0c143112b1bbe9d73790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-server-2013-and-2013-r2"></a>安裝 BizTalk Server 2013 和 2013 R2
列出安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的步驟。  
  
## <a name="before-you-get-started"></a>在開始之前

-   **帳戶名稱** – 您應該盡量使用預設帳戶名稱。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式會自動輸入預設帳戶。 如果在網域中有多個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組，請變更帳戶名稱以避免發生衝突。 如果您變更名稱，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]僅支援\< *NetBIOS 網域名稱*>\\<*使用者*> 服務帳戶和 Windows群組。  
  
-   **帳戶名稱與 BAM 管理 Web 服務** – [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援使用內建帳戶或無密碼的帳戶作為 BAM 管理 Web 服務使用者。 Web 服務會存取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫，而這類帳戶可能會帶來安全性威脅。  
  
    > [!NOTE]
    >  使用這類帳戶來設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可能會成功，但 BAM 管理 Web 服務會失敗。 內建帳戶或無密碼的帳戶可用於 BAM 應用程式集區。  
  
-   **BizTalk 組件檢視工具** – 不支援 64 位元平台。  
  
-   **安裝和解除安裝** – 解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，需要手動刪除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫。 如果以開發人員或評估員身分來安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請使用虛擬機器。 如果需要重新安裝，您可以輕鬆復原虛擬機器，而不需要解除安裝和刪除資料庫。  
  
-   **32 位元和 64 位元電腦** – 在 32 位元或 64 位元電腦上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時有幾項差異。 安裝和設定的內容涵蓋 32 位元和 64 位元的電腦， 但會註明任何差異。  
  
-   **工作群組** - 支援在工作群組環境中的單一電腦上安裝和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此時，SQL Server 與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能和元件都是在同一部電腦上安裝和設定。  
  
-   **終端機伺服器**：不支援使用在應用程式模式下執行的終端機伺服器來安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 請參閱 [KB 832027](http://support.microsoft.com/kb/832027)。  
  
-   **BAM 入口網站**  - 如果 BAM 入口網站是在執行 .NET Framework 2.0 的應用程式所使用的網站上設定，請為 BAM 入口網站建立新的網站：  
  
     [建立 IIS 7 網站](http://technet.microsoft.com/library/cc772350\(WS.10\).aspx)  
  
     [建立 IIS 8 網站](http://technet.microsoft.com/library/hh831515.aspx)  
  
     建立新的網站之後，請執行下列步驟：  
  
    1.  開啟 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態]。  
  
    2.  從 [BAM 入口網站] 清單中選取新的網站，以設定 BAM 入口網站。  
  
-   **社群補充**：請參閱：  
  
     [BizTalk Server 的主動性](http://msdn.microsoft.com/library/dn393929\(v=bts.10\).aspx)  
  
     [BizTalk Server 2013 R2: Installation and Configuration – Important considerations before set up the server (Part 1)](http://sandroaspbiztalkblog.wordpress.com/2015/01/04/biztalk-server-2013-r2-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)  
  
##  <a name="BKMK_Install"></a> 安裝 BizTalk Server  
  
1.  關閉所有開啟的程式。 以系統管理員身分執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式。  
  
2.  在 [開始] 功能表中，選取 [安裝 Microsoft BizTalk Server]。  
  
3.  在 [客戶資訊] 輸入您的使用者名稱、組織以及產品金鑰，然後選取 [下一步]。  
  
4.  在 [授權合約] 中接受授權合約，然後選取 [下一步]。  
  
5.  在 [客戶經驗改進計畫] 中，選擇您的參與偏好，再選擇 [下一步]。  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 參與「客戶經驗改進計畫」。 您可以選擇將您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時的相關實用資訊回報給 Microsoft。 收集的資料會是匿名形式，無法用來識別您的身分。 加入這項計畫後，Microsoft 也會收集使用統計資料。 如果您參與這項計畫，將能協助我們改善 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 各項功能的可靠性和效能。 如需這項計畫和其隱私權原則的詳細資訊，請參閱 [Microsoft BizTalk Server CEIP 隱私權原則](http://go.microsoft.com/fwlink/p/?LinkId=188553)。  
  
6.  在 [元件安裝] 中，檢閱可用的元件，並選取要安裝的元件：  

    |功能|描述|  
    |-------------|-----------------|  
    |**文件集**|SDK 範例與公用程式的核心文件、教學課程、UI 參考 (F1 說明)、程式設計師參考以及使用方式指示。|  
    |**伺服器執行階段**|適用於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的基本執行階段服務。|  
    |**BizTalk EDI/AS2 執行階段**|執行階段服務可原生支援電子資料交換 (EDI) 的資料交換和 Applicability Statement 2 (AS2) 資料傳輸的傳訊功能。 **注意：**只有在已選取 [伺服器執行階段] 功能時，才能選取此項目。|  
    |**Windows Communication Foundation (WCF) 配接器執行階段**|可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 WCF 架構的應用程式通訊的配接器。 **注意：**只有在已選取 [伺服器執行階段] 功能時，才能選取此項目。|  
    |**入口網站元件**|入口網站元件是一組功能，可讓商務分析師利用商務資料進行溝通、合作及決策工作。|  
    |**商務活動監控**|也稱為 BAM，其為一組功能，可讓商務使用者即時檢視不同的商務程序，以制定重要的商業決策。 **注意：**只有在已選取 [入口網站元件] 功能時，才能選取此項目。|  
    |**系統管理工具和監視**|為在本機電腦和遠端伺服器上管理與監視 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的必要元件。|  
    |**Windows Communication Foundation (WCF) 系統管理工具**|選取此功能會安裝 WCF 元件適用的系統管理服務。 **注意：**只有在已選取 [Administrative Tools and Monitoring (系統管理工具和監視)] 功能時，才能選取此項目。|  
    |**開發者工具與 SDK**|可快速建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案的範例與公用程式。 其中包括 SDK 範例與支援的文件、結構描述和對應設計工具、Visual Studio 專案範本。 **重要事項：**如果您打算執行任何開發工作，則必須安裝此元件。 如果未安裝**開發者工具與 SDK** 元件，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所使用的 Visual Studio 擴充功能將無法運作。|  
    |***其他軟體***||  
    |**企業單一登入 (SSO) 管理模組**|SSO 分支機構應用程式和其對應適用的管理介面。|  
    |**企業單一登入主要密碼伺服器**|存放主要密碼的 SSO 伺服器。 系統中所有其他 SSO 伺服器皆會從這部伺服器取得主要密碼。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境必須具備主要密碼伺服器。|  
    |**商務規則元件**|用來撰寫商務規則引擎使用的原則。|  
    |**MQSeries 代理程式**|提供 BizTalk Adapter for MQSeries 和 Windows 的 MQSeries Server 之間的通訊。|  
    |**Windows SharePoint Services 配接器 Web 服務**|**已被取代**。 使用安裝在 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 電腦上的 IIS Web 服務時，[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器會處理透過 Microsoft SharePoint 傳入與傳出的文件。<br /><br /> **建議**：請**不要**安裝。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 預設會使用在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上自動安裝的 SharePoint 用戶端物件模型 (CSOM) 可轉散發套件；如[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)所述。|  
    |**BAM Alert Provider**|設定 BAM 警示。<br /><br /> 使用 [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] 或 [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] SP1 的 BAM 警示時，您必須設定 Database Mail 功能。 您無法使用 SQL Server Notification Services。|  
    |**BAM 用戶端**|可讓商務使用者利用 BAM 的用戶端軟體。|  
    |**BAM Eventing**|為 Windows Workflow Foundation 和 Windows Communication Foundation 的攔截器。 其中也包括 BAM 事件 API，可將事件從自訂的應用程式傳送到 BAM 資料庫。|  
    |**專案建置元件**|此工具可讓您建置 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 方案，而不使用 Visual Studio。|  

7. 接受預設安裝位置，或選取 [瀏覽] 並輸入要安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的位置。 選取 [下一步]。  
  
8.  如果電腦缺少 ADOMD.NET 這類必要元件，安裝程式可安裝必要的可轉散發套件。 您可以：  
  
    -   選取 [從 Web 自動安裝必要的可轉散發套件]。  
    
         OR  
  
    -   如果您已下載封包檔，則可以選取 [從封包檔自動安裝必要的可轉散發套件]。 如果您選取此選項，則可以瀏覽到封包檔的位置。  
  
9.  在 [摘要] 中，確認元件皆正確。 若要啟用在系統重新開機之後自動登入的功能，請選取 [設定] 並輸入您的登入資訊。 只有在安裝期間的重新開機時，才會啟用自動登入，待安裝完成時即會停用。  
  
10. 選取 [安裝] 開始安裝程序。  
  
11. 在 [Microsoft Update 安裝] 中，選擇您的偏好，再選取 [下一步]。  
  
12. 在 [已完成安裝] 畫面上，取消選取 [啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態] 核取方塊，然後選取 [完成]。  
  
## <a name="additional"></a>其他  
  
-   安裝 SQL Server 之後，SQL Server 安裝程式會將系統管理員權限授與您已登入的帳戶。 因為安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也需要這些權限，所以您必須執行下列其中一項步驟：  
  
    -   使用您在安裝 SQL Server 時所使用的相同帳戶。  
  
    -   將系統管理員權限授與所登入的帳戶。  
  
-   下載 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的自我解壓縮 EXE 之後，會開啟安裝指南。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 Setup.exe 與安裝指南位於相同位置。  
  
-   您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 積存影像設定 [!INCLUDE[winazure](../includes/winazure-md.md)] 虛擬機器，而不需在實體電腦上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 請參閱[在 Azure 虛擬機器上設定 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)。  
  
-   如需如何使用命令提示字元安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的步驟，請參閱[附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)。  
  
 
## <a name="see-also"></a>另請參閱  
   
 [附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)   
 [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [附錄 C：可轉散發的封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [附錄 D︰建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)