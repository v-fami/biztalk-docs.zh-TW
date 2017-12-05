---
title: "在多重電腦環境中安裝 BizTalk Server |Microsoft 文件"
description: "多伺服器安裝和設定指南 BizTalk 和 SQL Server 安裝在不同的電腦，包括 BAM 時"
ms.custom: 
ms.date: 11/30/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d0e707-6b9e-49e1-9f17-19b3bac1229e
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26100e268e6dd657369bb044461c42a6ba0b5a9c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="install-biztalk-server-in-a-multi-computer-environment"></a>在多電腦環境中安裝 BizTalk Server

## <a name="overview"></a>概觀

在規劃 Microsoft® BizTalk® Server 的多重電腦安裝時需要考量許多事項。 經常存在於網路基礎結構和 BizTalk Server 必須與其他網路應用程式並存。 本指南將說明一些適用於多重電腦的 BizTalk Server 和分散式部署中的商務活動監控 (BAM) 安裝的考量。 這項資訊可協助您規劃的安裝和設定 BizTalk Server 商務活動監控 (BAM) 和應用程式和元件而定。

單一伺服器安裝指南包含重要的程序並不會重複本文件的詳細背景資訊。 比方說，下列資訊會在單一伺服器安裝指南中詳細討論：

- 詳細的安裝程序
- BizTalk Server 功能和相依性的描述
- BizTalk Server 基本組態設定詳細資料
- 軟體和硬體需求
- 封包檔的可轉散發元件清單

## <a name="high-availability"></a>高可用性
BizTalk Server 提供高可用性解決方案會使用網路負載平衡 (NLB) 叢集和容錯移轉叢集和 SQL Server Always On 可用性群組 (AG) 的使用。 高可用性解決方案有助於縮短停機時間，如果發生硬體或軟體失敗。 

**NLB 和容錯移轉叢集**彼此互補中複雜的架構。 NLB 叢集用於平衡載入前端 Web 伺服器之間的要求。 容錯移轉叢集提供高可用性的 BizTalk server 內含式主控件、企業單一登入主要密碼伺服器和 BizTalk Server 資料庫。 這通常是在內部部署環境。 下列是實用的資源： 

* [BizTalk Server： 高可用性求生指南](http://social.technet.microsoft.com/wiki/contents/articles/6532.biztalk-server-high-availability-survival-guide.aspx)

* [使用 Windows Server 容錯移轉叢集或 Windows Server 叢集改進 BizTalk Server 中的容錯功能](http://go.microsoft.com/fwlink/p/?LinkId=154499)

**SQL Server Alwayson 在 AG**可用在內部部署環境及 Azure 虛擬機器。 AG 支援 BizTalk Server 2016 中，以開始，而且任何較新版本的 BizTalk Server 中支援。 AG 包含主要資料庫複本和次要資料庫複本。 次要資料庫複本提供備援和容錯移轉時，BizTalk Server 會連接到主要資料庫複本。 [Alwayson 可用性群組 (SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)提供 AG 運作的詳細資訊。 

[BizTalk HA 使用 SQL Server Alwayson 在 AG](../core/high-availability-using-sql-server-always-on-availability-groups.md)從 BizTalk 觀點來看更多詳細資料。

## <a name="separate-runtime-and-administration"></a>個別的執行階段和管理
BizTalk Server 在生產環境中支援不同的安裝案例。 例如，您可以在某一部電腦上安裝、設定並部署僅含執行階段的安裝，而在第二部電腦上只安裝管理工具。

執行僅管理工具安裝期間，系統會安裝下列元件：BizTalk 管理主控台、BM.exe 和 BTSDeploy.exe。 建立系統管理工具僅限 BizTalk Server 安裝時，請考慮下列：

- SQL Server Agent 必須在裝載 BizTalk Server MessageBox 資料庫的所有電腦上執行。 SQL Server 代理程式需要追蹤 BizTalk Server 傳訊引擎中的訊息內文。

- 當您執行 BizTalk Server 組態精靈時，您會建立 Analysis Services 資料庫。

- 不支援使用 BizTalk 追蹤資料庫搭配 SQL Server Analysis Services。

- 不支援使用 SQL Server Analysis Services 的具名執行個體。

若要安裝 BizTalk Server 僅管理工具，選取 僅**系統管理工具**在安裝期間。 安裝完成後，開啟自訂組態管理員，並加入現有的企業單一登入 (SSO) 系統和 BizTalk 群組。
頁面頂端

## <a name="enable-msdtc"></a>啟用 MSDTC
在多重電腦環境中安裝和設定 BizTalk Server 之前，請先啟用網路 DTC 存取和網路 COM+ 存取所有 BizTalk server 和 BizTalk Server 使用的任何遠端 SQL Server 執行個體。 請參閱[後設定步驟來最佳化您的環境](post-configuration-steps-to-optimize-your-environment.md)。

其他：

- 所有的 BizTalk server 和 SQL 伺服器群組中必須有相同遠端程序呼叫 (RPC) 的驗證層級套用。 當電腦使用不同的作業系統，會加入至工作群組，或位在互不信任的不同網域，則 DTC proxy 可能無法正確驗證 DTC。 請參閱[MSDTC 無法相互驗證](https://msdn.microsoft.com/library/ms686976(VS.85).aspx)。

- 如果使用防火牆，請開啟必要的 DTC 和 RPC 連接埠。 請參閱[服務概觀和網路連接埠需求適用於 Windows](http://support.microsoft.com/kb/832017)。

- 若要確保 DTC 設定正確無誤，請使用 DTC Tester 和 DTC Ping 工具。 這些工具，以及更多 DTC 疑難排解詳述在[BizTalk Server-MSDTC 問題疑難排解](https://social.technet.microsoft.com/wiki/contents/articles/2031.biztalk-server-troubleshooting-problems-with-msdtc.aspx)。

## <a name="remote-sql-server"></a>遠端 SQL Server
當遠端電腦上安裝 SQL Server:

- [SQL Server 管理工具](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)（較新的 SQL 版本） 或遠端 SQL Server 時，必須在本機 BizTalk Server 電腦上安裝 SQL Server 用戶端工具連接性 （較舊的 SQL 版本）。 SQL Server 工具會安裝與遠端 SQL Server 執行個體通訊所需要的用戶端程式庫。 本機 BizTalk Server 電腦上的 SQL Server 工具的版本必須是遠端的 SQL Server 已安裝的版本相同。

- 如果您打算從遠端使用 Analysis Services，必須在本機電腦上安裝 SQL Server OLAP 用戶端。 OLAP 用戶端可能會隨附[SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)。

- 遠端 SQL Server 必須在 BizTalk Server 組態期間執行。

- SQL Server 安裝程序期間所指定的 TCP 和 UDP 連接埠必須開啟 BizTalk Server 組態期間。

- 若要設定 BAM 工具，安裝 SQL Server 管理工具-基本 」 和 「 BizTalk BAM Server 上的完成。 如需有關設定和多重電腦環境中設定 BAM 的詳細資訊，請參閱[安裝及設定 BAM （商務活動監控） 在多重電腦環境中](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)。 

- 不支援的 SQL Server Analysis Services 具名執行個體。

### <a name="sql-server-topologies"></a>SQL Server 拓撲
在 BizTalk 伺服器上，或在另一個專用的 SQL Server 的伺服器上，可以在本機安裝 SQL Server。 大部分的實際執行案例包括 BizTalk Server 和 SQL Server 安裝在不同的電腦上。 

如需支援的 SQL Server 版本的清單，請參閱： 

* [BizTalk Server 2016 軟體需求](hardware-and-software-requirements-for-biztalk-server-2016.md) 
* [BizTalk Server 2013R2 和 2013年的軟體需求](hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

> [!IMPORTANT]
> 任何額外的 Service Pack 和 Windows 更新將受到支援，而且應該安裝。

### <a name="maintain-and-troubleshoot-databases"></a>維護和疑難排解資料庫

請參閱[如何維護和疑難排解 BizTalk Server 資料庫](http://support.microsoft.com/kb/952555)。

## <a name="business-activity-monitoring-bam"></a>商務活動監控 (BAM)
BizTalk Server 會提供一些工具，資訊工作者，其間的 BAM。 元件架構的基本了解可協助您規劃 BizTalk Server 安裝，利用提供給您的伺服器資源。
商務活動監控 (BAM) 是用來管理彙總、 警示與監視相關的商務計量，又稱為關鍵效能指標或 Kpi 的設定檔工具的集合。

BAM 是模組，可讓您端對端可見性到您的商務程序，以提供各種操作程序和交易的結果與狀態的相關資訊。 您可以使用 BAM 輸出來定位問題區域並在您的企業中解決問題。 如需 BAM 生命週期的詳細資訊，請參閱 < 商務活動監控 (BAM) 海報[BizTalk Server BAP 海報](https://www.microsoft.com/download/details.aspx?id=56123)。

BAM 包含下列層級：

| 層 | 用途 | 範例 | 安裝位置 |
|---| ---|---|---|
| 展示和工具 | 提供前端服務給商務使用者和開發人員。 顯示資料，讓商務使用者和開發人員定義和管理範本與設定檔。在其他函式。 | Office Excel 時，BAM 入口網站 | 商務使用者或開發人員工作站上安裝 Excel、 管理工具和自訂使用者介面。 建立 BAM 基礎結構上的 BAM 入口網站和自訂的 web 應用程式會安裝在伺服器上。 |
| Web 服務和處理 | 連結展示和資料庫層、實作商務規則和程序，以及進行資料彙總和分析。 | Windows SharePoint Services (WSS)、 交易夥伴管理 Web 服務、 BAM 管理 Web 服務和 BizTalk Server 引擎。 | 在伺服器上使用 IIS、 SQL Notification 服務，而且可能是自訂的 web 服務，根據應用程式。 在此伺服器上，或在具有三個或多部電腦的多個電腦設定中的伺服器上，也可以安裝 BizTalk 主控件服務。 |
| 資料庫和平台服務 | 資料儲存和擷取、安全性和驗證、網路功能，以及作業系統功能 | SQL Server、 Windows Server、 企業單一登入 (SSO)，並容錯移轉和 NLB 叢集 | 在具有 Windows Server、SQL Server 的伺服器上。 基於效能考量，這部伺服器通常不會執行 BizTalk 主控件服務。 |

### <a name="install-bam"></a>安裝 BAM
逐步指南：[安裝及設定 BAM （商務活動監控） 在多重電腦環境中](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

為了要更容易了解 BAM、安裝與設定程序及相依性，將如下表所述分割成三部分 BizTalk Server 環境：

| 執行階段環境 | 設計階段環境 | 使用時間環境 |
|---|---|---|
| 基本的 BizTalk Server 執行階段環境可以包含下列伺服器： <ul><li>BizTalk Server</li><li>SQL Server</li><li>BizTalk BAM Server</li><li>網頁伺服器</li></ul> | BAM 開發和部署程序期間包含三個角色。 角色包括： <ul><li>商務分析師</li><li>商務系統管理員</li><li>應用程式開發人員</li></ul> | 實作並部署 BAM 解決方案之後，商務使用者可以檢視各種報告工具所產生的報告。 這些工具包括： <ul><li>BAM 入口網站 </li><li>SQL Server Reporting Services</li><li>Microsoft PerformancePoint 監控伺服器</li><li>自訂 BAM 報告應用程式</li></ul> |

下表描述要安裝的 BAM 元件：

|類別目錄 |BAM 元件|目的|
|---|---|---|
| 入口網站元件 | 商務活動監控 | 選取商務活動監控元件安裝的軟體，可讓商務使用者即時檢視他們的異質商務程序，讓他們能夠制定重要的商務決策。 |
| 其他軟體 | BAM 警示 | 安裝必要的軟體，讓 BizTalk Server 提供商務活動監控 (BAM) 警示。 <br/><br/>在 BizTalk Server 2013 R2 及更新版本的 BAM 警示使用 SQL Server Database Mail。 不使用或不支援 SQL Notification Services。<br/><br/>在 BizTalk Server 2013 與 SQL Server 2012 上的 BAM 警示使用 SQL Notification Services。 在 BizTalk Server 2013 與 SQL Server 2008 R2 上的 BAM 警示使用 SQL Notification Services。 |
| | BAM 用戶端 | 選取 BAM 用戶端元件以安裝必要的用戶端軟體，讓商務使用者可以使用 BizTalk Server 的商務活動監控功能。 | 
| | BAM Eventing | 選取 BAM-Eventing Support 元件安裝軟體以獲得 BAM-Eventing 攔截器供 Windows Workflow Foundation 和 Windows Communication Foundation 使用。 選取此元件也會安裝 BAM Event API，用來從自訂應用程式傳送事件到 BAM 資料庫。 BAM-Eventing Support 是 BizTalk Server 中的商務活動監控功能的一部分。 | 

### <a name="configure-bam"></a>設定 BAM
逐步指南：[安裝及設定 BAM （商務活動監控） 在多重電腦環境中](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

開啟 BizTalk Server 組態，然後選擇[自訂組態](configure-biztalk-server.md)。 在自訂組態中，您可以設定進階的選項和選擇性地設定或取消設定各項功能。 

### <a name="install-and-configure-sql-server-for-bam"></a>安裝和設定 BAM SQL Server

在[什麼是新增、 安裝、 設定及升級](biztalk-server-what-s-new-installation-configuration-and-upgrade.md)，您可以： 

- 請參閱 BizTalk Server 中，包括支援的 SQL Server 版本支援的軟體需求
- 安裝先決條件軟體，包括 SQL Server。 如需 SQL Server 特定安裝步驟，請參閱[安裝 SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup)或[安裝 SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx)。

除了 BizTalk Server 核心函式所需的資料庫服務，BAM 也需要：

- SQL Server Analysis Services (SSAS)

- SQL Server Integration Services (SSIS)

- SQL Server Database Mail 或 SQL Server Notification Services (SSNS)

##### <a name="configure-ssis"></a>設定 SSIS
如果您的 SQL Server 安裝在 BizTalk Server 以外的電腦上，就需要設定 SSIS。 在這個工作中，您必須設定 SSIS 以使用遠端 SQL Server 上的 msdb 資料庫。

1. 開啟命令提示字元。

2. 將目錄變更到 %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn。
 
3. 執行下列命令： notepad MsDtsSrvr.ini.xml

4. 在 [記事本] 內的文字更新 「<ServerName>"SQL Server 的主機名稱的標記。 儲存變更。

5. 從命令提示字元中，執行下列命令： net stop MsDtsServer

6. 從命令提示字元中，執行下列命令： net start MsDtsServer

    **其他**:  
    根據預設，Integration Services 服務被設定來管理儲存在本機 Database engine 的預設執行個體的 msdb 資料庫中的封裝。 若要管理儲存在資料庫引擎具名執行個體或遠端執行個體中的封裝，或儲存在多個資料庫引擎執行個體中的封裝，您就必須修改組態檔。 例如，您可以建立多個類型為 SqlServerFolder 的根資料夾來管理資料庫引擎中多個執行個體之 msdb 資料庫的封裝，您也可以修改組態檔以允許繼續執行封裝。 此選項會讓物件總管中顯示更多根資料夾，或 Integration Services 服務所管理的檔案系統中指定不同或多個資料夾。

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTS\ServiceConfigFile`登錄機碼指定的位置和 Integration Services 服務使用的設定檔的名稱。 此登錄機碼的預設值為 C:\Program Files\Microsoft SQL Server\100\DTS\Binn\ MsDtsSrvr.ini.xml。 您可以將此登錄機碼的值更新為使用不同的組態檔名稱和位置。

#### <a name="configure-bam-databases"></a>設定 BAM 資料庫
您可以在不同的電腦上設定 BAM 主要匯入、BAM 封存、BAM 星狀結構描述、BAM 分析和 BAM Notification Services 應用程式資料庫。 以下是當 SQL Server 安裝在 BizTalk Server 以外的電腦上時的軟體需求：

| BAM 功能 | 功能組態 | BizTalk Server | SQL Server | 
|---|---|---|---|
|BAM 工具 | BAM 主要匯入資料表和 BAM 封存資料庫 | ADOMD.NET SQL Server Integration Services | 支援的 SQL Server 版本。 請參閱[新安裝、 設定及升級](biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。|
| BAM 工具| 啟用 BAM 彙總的 Analysis Services| SQL Server Integration Services| SQL Server Analysis Services| 
| BAM Notification Services 應用程式資料庫| BAM 警示| BAM 警示 <br/>中所列的需求[什麼是新增、 安裝、 設定及升級](biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。| 如果使用 SQL Server 2012 或 SQL Server 2014，請設定 SQL Server Database Mail。 如果使用 SQL Server 2008 R2，請安裝 SQL Server 2005 Notification Services 引擎元件。<br/><br/>BAM 警示需求會記載於備妥電腦準備安裝。

> [!NOTE] 
> 用於 OLAP 服務的服務帳戶應擁有 BAM 星狀結構描述資料庫上的 db_datareader 權限。

##### <a name="notification-services--biztalk-2013--sql-server-2008-r2-only"></a>通知服務 – BizTalk 2013 / 僅限 SQL Server 2008 R2

> [!IMPORTANT]
> 如果使用 SQL Server 2008 R2，僅適用於這一節。

您可以在多重電腦環境中安裝 SQL Server Notification Services，而且其中 Notification Services 的提供者、產生器和散發者角色可在不同的電腦上。 下面將說明該實例中的相依性：

- AggregationEventProvider.dll 應該安裝在裝載提供者角色的電腦上。 當您在 BizTalk server 安裝期間安裝 BAM 警示彙總事件提供者時，會安裝此.dll 檔案。 如果已安裝 BizTalk 執行階段、管理工具，或開發者工具與 SDK，BAM 警示彙總事件提供者便會存在。

- 裝載散發者角色的電腦上必須有 EmailNotification.xslt 和 FileNotification.xslt。 您可以從現有的 BizTalk Server 中的下列路徑複製檔案： \Program Files\Microsoft BizTalk Server*版本*\Tracking

- 更新 Notification Services 應用程式定義檔 （.adf 檔） 與.xslt 檔案在裝載散發者角色的電腦上的確切位置。 

**更新應用程式定義檔 （.adf 檔）**:  

1. 在電腦上安裝 BizTalk Server，開啟 Notification Services 命令提示字元。
2. 瀏覽至 files\microsoft BizTalk Server*版本*\Tracking。
3. 執行 ProcessBamNsFiles.vbs 來建立初始 .adf 檔案。
4. 將 .adf 檔案的路徑修改成與 .xslt 檔案的路徑相同。
5. 再次執行 ProcessBamNsFiles.vbs 來更新 .adf 檔案。
6. 重新啟動 BAMAlerts NT 服務。

##### <a name="bam-scale-out-alerts-topology"></a>BAM 向外擴充警示拓撲
如果您要升級現有的 BAM 向外延展警示拓撲，BizTalk Server 2013，然後執行每一部伺服器上的下列步驟：

1. 停止 Notification Service，然後取消註冊 Notification Services 的執行個體。
    1. 在**程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**.
    1. 在命令提示字元中，輸入： `net stop NS$<instance_name>`。 例如，輸入： `net stop NS$BamAlerts`。
    1. 若要取消註冊執行個體，請輸入下列命令： `nscontrol unregister -name BamAlerts`。 

        取消註冊執行個體會移除登錄項目、移除 NS$instance_name 服務 (如果有)，並刪除服務的效能計數器。

2. 將具有 Notification Services 執行個體的伺服器升級為更高版本的 SQL Server 2005 Notification Services。

3. 若要根據您進行升級的 SQL Server 版本將 BAM 資料庫的移轉，執行位於 BizTalk Server Tracking 資料夾中的移轉資料庫命令 bm.exe 程式。 例如，如果 SQL Server 2005 升級到 SQL Server 2008 R2 時，執行下列系統管理認證在命令提示字元中： `bm.exe migrate-sql –From:sql2005 –To:sql2008 –NSUser:<username>`。

4. 重新註冊 Notification Service，移轉程式 (bm.exe) 已被使用在伺服器以外的所有伺服器上。

    1. 在**程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**.
    2. 在命令提示字元中，輸入：`nscontrol register -name BamAlerts -server <NS DB Server> -service -serviceusername "<NSServiceUserName>" -servicepassword "<NSServicePassword>"`

    如此可讓 Notification Services 登入正確的資料庫 (nscontrol 將這項資訊保存在服務電腦的登錄中)。

    > [!IMPORTANT] 
    > 請記得使用新的 Notification Services 資料庫伺服器時重新註冊服務-server 選項中。 此外，使用新的 Notification Services 服務的相同使用者名稱與舊。

5. 驗證 BAM 警示： 開啟**Notification Services 命令提示字元**和型別： `nscontrol.exe status –name BAMAlerts –server <NS DB Server>`。

### <a name="bam-portal"></a>BAM 入口網站
入口網站元件是一組商務人員用來溝通、 共同作業，和做出決策，使其能夠互動時，服務設定和監控商務程序與工作流程。 若要使用這項功能，安裝網際網路資訊服務 (IIS)。 IIS 需求[什麼是新增、 安裝、 設定及升級](biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。

### <a name="bam-add-in-from-excel"></a>BAM 增益集從 Excel
[新增或移除增益集](https://support.office.com/article/add-or-remove-add-ins-0af570c4-5cf3-4fa9-9b88-403625a0b460)列出適用於 Excel 的步驟。 BAM 增益集名稱是**商務活動監控**。

### <a name="configure-multiple-biztalk-groups-to-use-a-single-bam-database"></a>設定多個 BizTalk 群組，以使用單一 BAM 資料庫
跨多個 BizTalk 群組共用 BAM 資料庫：

1. 設定第一個具有 BAM 功能的 BizTalk 群組。 這些功能包括 BAM 工具、 BAM 分析資料庫、 BAM 警示和 BAM 入口網站。

2. 設定後續的 BizTalk 群組，並執行 BizTalk Server 組態精靈中的下列動作：

    1. 選取**BAM 工具**，然後選取**啟用商務活動監控工具**和**啟用 BAM 彙總的 Analysis Services**核取方塊。

    2. 變更**伺服器名稱**和**資料庫名稱**的 BAM 資料存放區，以符合設定第一個 BizTalk 群組時所使用的相同名稱。

    3. 選取**BAM 警示**，然後選取 **啟用 BAM 警示**。

    4. 變更 BAM 警示的服務帳戶，因此它是空白的使用者名稱和密碼。

    5. 變更 BAM 警示 SMTP 伺服器時，BAM 警示檔案位置，SQL Server 警示資料庫，並警示資料庫名稱以符合設定第一個 BizTalk 群組時所使用的相同名稱的前置詞。

    > !請注意] 相同的主要匯入資料表 (PIT) 可以使用，但具有不同的 BAM 封存、 BAM 分析和星狀結構描述資料庫。 不過這個選項會影響所有使用相同 PIT 的群組。

3. 選取**BAM 入口網站**，然後選取**啟用 BAM 入口網站**核取方塊。

    > [!NOTE]
    > 此畫面上的所有欄位皆為唯讀，因為 BAM 主要匯入資料庫與 BAM 入口網站間為一對一的關係。 多個 BizTalk 群組共用 BAM 入口網站時設定對相同的 BAM 資料庫。

4. 選取**套用組態**。

### <a name="bam-client-software-requirements"></a>BAM 用戶端軟體需求
- Web 用戶端，您需要 Internet Explorer 和 Office Web 元件 11 版本 4.0 或更新版本。

- 如果您正在執行 web 用戶端，並使用 SQL Server 2008 R2 Analysis Services，安裝 Microsoft SQL Server 2008 R2 Analysis Services 10.0 OLE DB 提供者。 

- 是 Excel 用戶端，您需要 Microsoft Excel 和 BAM Excel 增益集提供與 BizTalk Server。


## <a name="groups-and-service-accounts"></a>群組和服務帳戶
手動建立所有的網域群組和帳戶的多重電腦安裝中設定 BizTalk Server 之前。 建立這些群組與帳戶時下列資訊非常有用。

在多重電腦環境中，BizTalk Server 僅支援網域群組和網域服務帳戶。 

- BizTalk Server 僅支援<NetBIOSDomainName>\<使用者 > 名稱格式的 Windows 群組和服務帳戶。

- BizTalk Server 僅支援 Active Directory 網域群組和使用者帳戶在多重電腦組態。 網域群組包括「網域本機群組」、「全域群組」及「萬用群組」，單一電腦及多重電腦環境中都支援這些群組。

- 一般情況下，因為它們的使用需要的所有伺服器，包括 BizTalk Server 基礎結構中的 SQL 伺服器屬於相同的網域，不是建議網域本機群組。 這個考量不適用於所有伺服器和使用者帳戶都位於單一網域中的小型網路。 [Active Directory 群組](http://technet.microsoft.com/library/cc733001.aspx)提供詳細資訊。

- 當您安裝並設定在多重電腦環境中的 BizTalk Server 不支援內建帳戶，例如 NT AUTHORITY\LOCAL SERVICE、 NT AUTHORITY\NETWORK SERVICE、 NT AUTHORITY\SERVICE、 NT AUTHORITY\SYSTEM 和 Everyone。

- 執行 BizTalk Server 組態的使用者必須屬於下列使用者群組： 本機電腦的 SQL Server 電腦上，使用 BizTalk Server 系統管理員的網域群組的系統管理員群組上的 Administrators 群組群組，以及用於 SSO Administrator 群組的網域群組。

- 可能的話，請使用在安裝期間建立的預設帳戶名稱。 BizTalk Server 安裝程式會自動設定成使用預設帳戶安裝的元件。 雖然使用預設名稱可簡化安裝和設定作業，但是這種作法不一定總是可行。 例如，可以有多個作用中的網域樹系中的 BizTalk Server 群組。 在此情況下，您必須修改帳戶名稱，以避免發生衝突。 或者，您的組織可能會使用命名標準的服務和使用者帳戶，讓您變更要符合標準的預設帳戶。

### <a name="windows-groups"></a>Windows 群組
下表列出的 Windows 群組和 BizTalk Server 使用其成員資格。 本表也可以用來識別群組的「SQL Server 角色」或「資料庫角色」。

| 群組 | 群組描述 | 成員資格 | SQL Server 角色或資料庫角色 | 
| ---|---|---|---|
| SSO 系統管理員 | 「企業單一登入」(SSO) 服務的系統管理員。 [指定 SSO 系統管理員和分支機構系統管理員帳戶](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)更多詳細資訊。 | 包含「企業單一登入服務」的服務帳戶。 包含需要設定及管理 BizTalk Server 和 SSO 服務之能力的使用者/群組。包含可在設定 SSO 主要密碼伺服器時用來執行「BizTalk 組態管理員」的帳戶。 | **db_owner** sso 的 SQL Server 資料庫角色 <br/><br/>**securityadmin** SSO 所在的 SQL Server 的 SQL Server 角色。 |
| SSO 分支機構系統管理員 | 特定 SSO 分支機構應用程式的系統管理員。 可以建立/刪除 SSO 分支機構應用程式、 管理使用者對應，並設定認證的分支機構應用程式使用者。 | 沒有包含服務帳戶。 包含 BizTalk Server 系統管理員使用的帳戶。| |
|BizTalk Server 系統管理員 | 擁有執行管理工作所需的最低權限。 可以部署解決方案；管理應用程式；以及解決訊息處理問題。 若要執行配接器、接收和傳送處理常式以及接收位置的管理工作，必須將「BizTalk Server 系統管理員」新增到「單一登入分支機構系統管理員」。 請參閱[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)。 | 包含需要設定及管理 BizTalk Server 之能力的使用者/群組。 | **BTS_ADMIN_USERS**下列資料庫中的 SQL Server 資料庫角色：<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/>**db_owner**針對下列資料庫的 SQL Server 資料庫角色：<br/>BAMStarSchema<br/>BAMPrimaryImport<br/>BAMArchive<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**NSAdmin**下列資料庫中的 SQL Server 資料庫角色： <br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>下列資料庫中的 SQL Server 資料庫角色： <br/>BizTalkDTADb<br/>BizTalkMgmtDb。 <br/><br/>**OLAP 系統管理員**裝載 BAMAnalysis OLAP 資料庫的電腦上。 |
| BizTalk Server 操作員 | 具備低權限角色，僅有用來監控動作及針對動作進行疑難排解的存取權。 | 包含監控解決方案的使用者/群組。 沒有包含服務帳戶。 | **BTS_OPERATORS**下列資料庫中的 SQL Server 資料庫角色： <br/>BizTalkDTADb<br/>BizTalkEDIDb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb | 
| BizTalk 應用程式使用者 | 「組態管理員」建立的第一個「內含式 BizTalk 主控件群組」的預設名稱。 針對環境中的每個「內含式主控件」，各使用一個 BizTalk 主控件群組。 包括具有「內含式 BizTalk 主控件」(裝載 BizTalk Server 中的處理程序，BTSNTSvc.exe) 存取權的帳戶。 | 包含「BizTalk 內含式主控件執行個體」(屬於「內含式 BizTalk 主控件群組」被指定到的主控件) 的服務帳戶。  | **BTS_HOST_USERS**下列資料庫中的 SQL Server 資料庫角色：<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/> **BAM_EVENT_WRITER** BAMPrimaryImport 中的 SQL Server 資料庫角色。 | 
| BizTalk 外掛式主控件使用者 | 「組態管理員」建立的第一個「外掛式 BizTalk 主控件群組」的預設名稱。 不在 BizTalk Server 上執行的外掛式 BizTalk 主控件，如 HTTP 和 SOAP。 針對環境中的每個「外掛式主控件」，各使用一個 BizTalk 外掛式主控件群組。 | 包含「BizTalk 外掛式主控件執行個體」(屬於「外掛式 BizTalk 主控件群組」被指定到的主控件) 的服務帳戶。 | **BTS_HOST_USERS**下列資料庫中的 SQL Server 資料庫角色：<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport | 
| EDI 子系統使用者 | 擁有 EDI 資料庫的存取權。 | 包含 BizTalk 基底 EDI 服務的服務帳戶。 | **EDI_ADMIN_USERS** BizTalkEDIDb 中的 SQL Server 資料庫角色。 | 
| BAM 入口網站使用者 | 可以存取 BAM 入口網站。 | 這個角色預設使用 Everyone 群組。 沒有包含服務帳戶。 |  | 
| 啟用 BizTalk SharePoint 配接器的主控件 | 可以存取 Windows SharePoint Services 配接器 Web 服務。 | 包含 BizTalk 主控件執行個體，若要使用 SharePoint 配接器的服務帳戶。 |  | 
| BizTalk B2B 操作員群組 | BizTalk 角色，可降低系統管理員執行所有合作對象管理作業的負擔。 此角色可讓 Windows 使用者與角色關聯，以執行所有合作對象管理作業。 | 包含必須能夠設定和管理 BizTalk Server TPM 資料並監視解決方案的使用者/群組。 | **BTS_OPERATORS**下列資料庫中的 SQL Server 資料庫角色： <br/>BizTalkDTADb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BAMPrimaryImport |

### <a name="user-and-service-accounts"></a>使用者和服務帳戶
下表列出 BizTalk Server 使用的 Windows 使用者或服務帳戶以及群組分支機構。 它也會識別 SQL Server 角色或資料庫角色的帳戶。

| 使用者| 使用者描述| 群組分支機構 | SQL Server 角色或資料庫角色| 
| ---|---|---|---|
| 企業單一登入服務 | 用以執行會存取 SSO 資料庫之「企業單一登入服務」的服務帳戶。 | SSO 系統管理員 | | 
| BizTalk 主控件執行個體帳戶 | 用以執行 BizTalk 內含式主控件執行個體 (BTNTSVC) 的服務帳戶。 | BizTalk 應用程式使用者 | | 
| BizTalk 外掛式主控件執行個體帳戶 | 用以執行「BizTalk 外掛式主控件執行個體」(HTTP/SOAP) 的服務帳戶。 | BizTalk Isolated Host UsersIIS_WPG | | 
| 規則引擎更新服務 | 用以執行會從規則引擎資料庫接收部署/解除部署原則通知之「規則引擎更新服務」的服務帳戶。| | **RE_HOST_USERS** BizTalkRuleEngineDb 中的 SQL Server 資料庫角色。| 
| BAM Notification Services 使用者 | 用以執行會存取 BAM 資料庫之 BAM Notification Services 的服務帳戶。 | SQLServer2005NotificationServicesUser $<ComputerName> | **NSRunService**下列資料庫中的 SQL Server 資料庫角色：<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementNSReader** BAMPrimaryImport 的 SQL Server 角色。 | 
| BAM 管理 Web 服務使用者 | 可讓 BAM 管理 Web 服務 (BAMManagementService) 存取各種 BAM 資源的使用者帳戶。 BAM 入口網站登入以管理警示、 取得 BAM 定義 XML 和 BAM 檢視 BAM 入口網站的使用者認證呼叫 BAMManagementService。 | IIS_WPG | **NSSubscriberAdmin**下列資料庫中的 SQL Server 資料庫角色：<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementWS** BAMPrimaryImport 的 SQL Server 角色。 | 
| BAM 應用程式集區帳戶| 裝載 BAM 入口網站的 BAMAppPool 的應用程式集區帳戶。 | IIS_WPG | | 

> [!IMPORTANT]
> 如需有關 Windows 群組和 BizTalk Server 中所使用的服務帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。

## <a name="databases-list"></a>資料庫清單
以下是 BizTalk Server 中所使用的 SQL Server 資料庫清單：

| 資料存放區名稱 | 預設資料庫名稱 | 數量 | 成長 | Description | 
| ---|---|---|---|---|
| SSO 資料庫 | SSODB | 低 | 低 | 這個「企業單一登入」認證資料庫會安全地儲存使用者名稱和密碼。| 
| BizTalk 管理資料庫 | BizTalkMgmtDb | 低 | 低 | 這個資料庫是所有 BizTalk Server 執行個體的中央中繼資訊存放區。| 
| BizTalk MessageBox 資料庫 | BizTalkMsgBoxDb | 高 | 中 | BizTalk Server 引擎使用這個資料庫的路由、 佇列、 執行個體管理及其他各種工作。<br/><br/>**注意**<br/>自動更新統計資料、 自動建立統計資料和平行處理原則設定是刻意關閉的裝載 BizTalk Server BizTalkMsgBoxDB 資料庫的 SQL Server 資料庫執行個體。 請勿啟用這些設定。 | 
| BizTalk 追蹤資料庫 | BizTalkDTADb | 高 | 高 | 這個資料庫儲存了 BizTalk Server 追蹤引擎所追蹤的商務和狀況監控資料。 | 
| 規則引擎資料庫 | BizTalkRuleEngineDb | 低 | 低 | 這個資料庫是原則的儲存機制，原則即是相關規則和詞彙的集合。 詞彙為規則中關於資料參考的使用者易記、網域特定名稱的集合。 | 
| BAM 主要匯入資料庫 | BAMPrimaryImport | 中 | 中 | 這個資料庫會收集原始 BAM 追蹤資料。 | 
| BAM 封存資料庫 | BAMArchive | 中 | 中 | 這個資料庫會封存舊的商務活動資料。 建立 BAM 封存資料庫的 BAM 主要匯入資料庫中的商務活動資料累積降到最低。 | 
| BAM 星狀結構描述資料庫 | BAMStarSchema | 中 | 中 | 這個資料庫含有臨時資料表以及量值和維度資料表。 | 
| BAM Notification Services 應用程式資料庫 | BAMAlertsApplication | 中 | 中 | 這個資料庫包含 BAM 通知的警示資訊。 比方說，當您建立使用 BAM 入口網站警示時，項目會插入在此指定要與警示相關，以及其他支援的資料警示的條件和事件的資料庫中。 | 
| BAM Notification Services 執行個體資料庫 | BAMAlertsNSMain | 中 | 中 | 此資料庫包含指定的 notification services 如何連接到 BAM 正在監控系統的執行個體資訊。 | 

#### <a name="sql-server-databases-used-by-sharepoint"></a>SharePoint 所使用的 SQL Server 資料庫

| 資料存放區名稱 | 預設資料庫名稱 | 數量 | 成長 | Description | 
|---|---|---|---|---|
| Windows SharePoint Services 組態資料庫 | 使用者自訂 | 低 | 低 | 這個資料庫包含伺服器的所有全域設定。 | 
| Windows SharePoint Services 內容資料庫 | 使用者自訂 | 中 | 中 | 這個資料庫包含所有的網站內容，如清單項目及文件。 | 

## <a name="install-biztalk-a-multi-server-environment"></a>安裝 BizTalk 多伺服器環境

1. **安裝 Active Directory 網域服務**-在多重伺服器環境中安裝 BizTalk Server 所需的第一個步驟是安裝各種 BizTalk Server 群組和帳戶的 Active Directory 網域服務。 若要建立 Active Directory 網域，請參閱：

    - Windows Server 2012 及更新版本：[安裝 Active Directory 網域服務](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)
    - Windows Server 2008 R2: [AD DS 安裝與移除的逐步指南](https://technet.microsoft.com/library/cc755258(WS.10).aspx)

    > [!IMPORTANT]
    > BizTalk Server 群組中所述**使用者和服務帳戶使用 BizTalk Server 中**多伺服器環境中安裝 BizTalk Server 之前，就必須建立資料表 （在本主題）。

2. **視需要安裝多個執行個體的 SQL Server** – 如果負載需求使得您需要多個 MessageBox 資料庫，或您需要的 BizTalk Server I/O 負載分散到多個 SQL Server 執行個體，然後再安裝多個 SQL Server視需要的執行個體。 

    如需有關測試您的 BizTalk Server 環境和最佳化資料庫效能的詳細資訊，請參閱[BizTalk Server 效能最佳化指南](../technical-guides/biztalk-server-2013-performance-optimization-guide.md)。 

3. **視需要安裝多個 BizTalk Server 電腦到您的 BizTalk Server 群組**– 如果負載需求使得您需要多個 BizTalk Server 電腦到您的 BizTalk Server 群組，然後使用以 BizTalk Server Enterprise Edition在多部 BizTalk 伺服器擴充您的處理需求。 

    > [!IMPORTANT]
    > 許多 BizTalk Server 的企業層級功能，例如叢集、新增多部伺服器至群組和原生 64 位元處理，只有在 BizTalk Server 的 Enterprise 版本中才能使用。

4. **可安裝累計更新**-Windows Update 中所列的累計更新。 [知識庫文章 2555976](http://support.microsoft.com/kb/2555976) 列出可用的 Service Pack 和累積更新。

## <a name="cluster-considerations"></a>叢集的考量

- **叢集 MSDTC** – Microsoft Distributed Transaction Coordinator (MSDTC) 是所有 BizTalk Server 環境的中央元件。 如果 BizTalk Server 環境的其他元件已叢集，則建議也將 MSDTC 叢集。 

- **安裝 SQL Server 容錯移轉叢集**– BizTalk Server 資料庫中，提供高可用性/容錯，建議您使用 SQL Server 容錯移轉叢集上已安裝的 BizTalk Server 資料庫。 如需安裝 SQL Server 容錯移轉叢集的詳細資訊，請參閱： 

    * SQL Server 2016: [Alwayson 容錯移轉叢集執行個體 (SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)
    * SQL Server 2014: [Windows Server 容錯移轉叢集 (WSFC) 與 SQL Server](https://msdn.microsoft.com/library/ms189134(v=sql.120).aspx)

    一旦 SQL Server 設定為高可用性/容錯，則 SQL Server 叢集執行個體可以像任何其他 SQL Server 執行個體由 BizTalk Server 組態所參考。

- **企業單一登入主要密碼伺服器設定為叢集資源**– 企業單一登入主要密碼伺服器失敗可能導致 BizTalk Server 環境的全系統失敗。 建議透過將主要密碼伺服器設定為叢集資源，來將企業單一登入主要密碼伺服器設定為高可用性/容錯。 因為主要密碼伺服器在 BizTalk Server 環境中不是需要大量資源的元件，建議在相同叢集節點上叢集主要密碼伺服器為 SQL Server 執行個體。 如需企業單一登入主要密碼伺服器設定為叢集資源的詳細資訊，請參閱[叢集主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。 

- **將 BizTalk 主控件設定為叢集資源**– 執行多個 BizTalk Server 主控件執行個體提供高可用性/容錯。 因此除非在特別的情況下，並不建議將 BizTalk 主控件設定為叢集資源。 例如，您可以在配合高可用性/容錯，或在為特定 BizTalk Server 配接器提供排序傳遞時，將 BizTalk 主控件設定為叢集資源。 如需有關適當的 BizTalk 主控件設定為叢集資源的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。 另請參閱[如何將 BizTalk 主控件設定為叢集資源](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md)。 

- **叢集訊息佇列**– 請參閱[安裝並叢集化 MSMQ](https://blogs.msdn.microsoft.com/biztalknotes/2013/03/20/how-to-install-and-cluster-msmq-on-windows-server-2012/)。

- **叢集檔案系統**– 請參閱[如何叢集化檔案系統](http://go.microsoft.com/fwlink/p/?LinkId=189517)。

## <a name="use-scom"></a>使用 SCOM
適用於 Operations Manager 的 BizTalk Server 管理封包提供全方位探索及監控 BizTalk Server 元件和在多個機器中執行的應用程式。 如需有關 BizTalk Server 管理組件的詳細資訊，請參閱 http://www.microsoft.com/download/details.aspx?id=39617。
  
## <a name="next"></a>下一個  
[設定 BizTalk](configure-biztalk-server.md)