---
title: "準備您的電腦安裝 |Microsoft 文件"
ms.custom: 
ms.date: 2016-03-15
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a493c1a0ef38e9be5e229ff82f8773211adfe765
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-your-computer-for-installation"></a>準備安裝電腦
本主題列出藉由安裝和設定所有必要軟體，然後建立帳戶並設定權限，以便備妥電腦的步驟。  

> [!TIP] 
> 我們的整合 MVP 已準備了一份安裝必要條件與 BizTalk Server 的詳細逐步指南：[BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)。  
> 
> 不過，Microsoft 不建議您採取停用使用者帳戶控制 (UAC) 或 Windows 防火牆這類步驟。 
  
> [!IMPORTANT]
>  請依照所列的順序完成這些工作。  
  
##  <a name="BKMK_InstUpdates"></a> 安裝 Windows Update  
  
-   **Windows 7**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入 **Windows Update**。  
  
-   **Windows 8.1、[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 和 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2**：按一下鍵盤上的 Windows 鍵，並輸入 **Windows Update**。 按一下搜尋結果中的 **Windows Update**。  
  
 安裝更新之後，您可能需要重新啟動電腦。  
  
##  <a name="BKMK_IIS"></a> 啟用 Internet Information Services  
 Microsoft Internet Information Services (IIS) 為許多 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能提供了 Web 應用程式基礎結構，包括：  
  
-   HTTP 配接器  
  
-   SOAP adapter (SOAP 配接器)  
  
-   Windows SharePoint Services 配接器  
  
-   安全通訊端層 (SSL) 加密  
  
-   BAM 入口網站  
  
#### <a name="install-iis-75-on-windows-7-sp1"></a>在 Windows 7 SP1 上安裝 IIS 7.5  
  
1.  選取 [開始]。 在 [搜尋] 文字方塊中，輸入**程式和功能**，並加以開啟。  
  
2.  選取 [開啟或關閉 Windows 功能]。  
  
3.  選取 [Internet Information Services]，然後展開 [Internet Information Services]。 除了預設已核取的選項之外，另請核取下列項目：  
  
    -   **Web 管理工具**：另請核取：  
  
        -   IIS 6 管理相容性：  
  
            -   IIS 6 管理主控台  
  
            -   IIS Metabase 及 IIS 6 設定相容性  
  
        -   IIS 管理主控台  
  
    -   **World Wide Web 服務**：展開 [安全性] 再一併選取：  
  
        -   基本驗證  
  
        -   Windows 驗證  
  
4.  選取 [確定]。 完成後，請按一下 [關閉]。  
  
 [http://go.microsoft.com/fwlink/p/?LinkId=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) 也有列出在 Windows 7 中啟用 IIS 的步驟。  
  
#### <a name="install-iis-80-on-windows-8"></a>在 Windows 8 上安裝 IIS 8.0  
  
1.  按一下鍵盤上的 Windows 鍵。 輸入**程式和功能**，然後選取 [設定]。 在 [結果] 視窗中，選取 [程式和功能]。  
  
2.  選取 [開啟或關閉 Windows 功能]。  
  
3.  選取 [Internet Information Services]，然後展開 [Internet Information Services]。 除了預設已核取的選項之外，另請選取下列項目：  
  
    -   **Web 管理工具**：另請核取：  
  
        -   IIS 6 管理相容性：  
  
            -   IIS 6 管理主控台  
  
            -   IIS Metabase 及 IIS 6 設定相容性  
  
        -   IIS 管理主控台  
  
    -   **World Wide Web 服務**：展開 [安全性] 再一併核取：  
  
        -   基本驗證  
  
        -   Windows 驗證  
  
4.  按一下 [確定]。 完成後，請按一下 [關閉]。  
  
 [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) 也有列出在 Windows 8 中啟用 IIS 的步驟。  
  
#### <a name="install-iis-80-on-windows-server-2012"></a>在 Windows Server 2012 上安裝 IIS 8.0  
  
1.  開啟 [伺服器管理員]，然後按一下左窗格的 [儀表板]。  
  
2.  按一下 [新增角色及功能]。 您也可以從右上角的 [管理] 功能表開啟 [新增角色及功能]。  
  
3.  按一下 [在您開始前] 視窗中的 [下一步]。  
  
4.  在 [安裝類型] 視窗中，按一下 [角色型或功能型安裝]，然後按一下 [下一步]。  
  
5.  在 [伺服器選取項目] 視窗中，按一下 [從伺服器集區選取伺服器]，再按一下所需的伺服器，然後按一下 [下一步]。  
  
     [伺服器選取項目] 視窗會列出已使用 [伺服器管理員] 中的 [新增伺服器] 所新增的伺服器 。 根據預設，它會選取本機伺服器。 [將伺服器新增到伺服器管理員](http://go.microsoft.com/fwlink/p/?LinkID=241353)一文有列出在 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 中使用 [新增伺服器] 的步驟。  
  
6.  在 [伺服器角色] 視窗中，按一下 [網頁伺服器 (IIS)]。 如果出現提示，請按一下 [新增功能]，然後按一下 [下一步]。  
  
7.  在 [功能] 視窗中，保留預設啟用的選項，並注意下列事項：  
  
     **.Net Framework 3.5 功能**：[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] 和 [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] 可用來開發 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 的相關 .Net 應用程式。 通常，系統已安裝 **[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] 功能**。 如果您要使用 [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] 以在這台電腦上建立應用程式，也可以安裝 **.Net Framework 3.5 功能**。  
  
     **訊息佇列**：如果您是使用 MSMQ 配接器，可以核取 [訊息佇列] 以建立本機 MSMQ 存放區。  
  
     **SMTP 伺服器**：如果您是使用 SMTP 配接器，可以核取 [SMTP 伺服器] 以建立本機 SMTP 伺服器。  
  
     **Windows Identity Foundation 3.5**：使用 CSOM 安裝選項時，必須搭配 Windows Identity Foundation (WIF) 才能使用 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 配接器。 [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 配接器適用的 CSOM 安裝選項。  
  
     按一下 [下一步]。  
  
8.  在 [網頁伺服器角色 (IIS)] 視窗中，按一下 [下一步]。  
  
9. 在 [網頁伺服器角色 (IIS)] 下方的 [角色服務] 視窗中，按一下以下選項：  
  
     **安全性**：除了預設選項，另請按一下：  
  
    -   基本驗證  
  
    -   Windows 驗證  
  
     **應用程式開發**：若是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，則預設選項已足夠。 如果您在這台電腦上還主控其他 IIS 應用程式，請核取所需的角色。  
  
     **管理工具**：除了預設選項，另請按一下：  
  
    -   IIS 管理主控台  
  
    -   IIS 6 管理相容性：  
  
        -   IIS 6 Metabase 相容性  
  
        -   IIS 6 管理主控台  
  
     按一下 [下一步]。  
  
10. 在 [確認] 視窗中，按一下 [安裝]。 完成後，請按一下 [關閉]。  
  
 [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) 也有列出在 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 中啟用 IIS 的步驟。  
  
##  <a name="BKMK_XLS"></a> 安裝 Microsoft Office Excel  
  
1.  執行 Microsoft Office 安裝程式。  
  
2.  到達 [安裝類型] 畫面時，請選取 [自訂安裝]，然後選取 [下一步]。  
  
3.  在 [自訂安裝] 畫面上，選取 [Excel]，然後選取 [下一步]。  
  
4.  選取 [安裝]。  
  
5.  在 [安裝完成] 中，請選取 [完成]。  
  
 **其他**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只支援 32 位元版本的 Microsoft Office。  
  
-   必須搭配 Microsoft Office Excel，才能使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的商務活動監控 (BAM) 功能。 BAM Office Excel 活頁簿可定義您想監控的商務程序。 您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。  
  
-   若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用功能] 下的 [Visual Basic for Applications]。 否則，您可能會接收到「此活頁簿的 VBA 專案、ActiveX 控制項以及其他的程式設計相關功能已遺失」的錯誤。  
  
##  <a name="BKMK_VS"></a> 安裝 Visual Studio  
  
1.  以系統管理員身分執行 Visual Studio 安裝程式。  
  
2.  接受授權合約，然後按一下 [下一步]。  
  
3.  在 [要安裝的選擇性功能] 中，選取您需要的選項，然後選取 [安裝]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不需要任何選用的功能。  
  
4.  在 [完成] 頁面上，關閉視窗，或按一下 [啟動] 以開啟 Visual Studio。  
  
 **其他**  
  
-   如果您是先安裝 Visual Studio 之後才安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，接著再升級至 Visual Studio Team Explorer，則可能需要透過 [控制台] / [程式] 選項來修復 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝。  
  
-   Visual Studio 會自動安裝 Microsoft SQL Server Express，但 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並不會用到它。 因此最佳做法是解除安裝 Microsoft SQL Server Express。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具是以 Visual Studio 為基礎。 因此，您至少要先安裝 Visual Studio 的 Microsoft Visual C#® .NET 元件，然後再安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **開發者工具與 SDK**。  
  
-   如果您要將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在不需進行應用程式開發或偵錯的實際執行電腦 (僅限執行階段) 上，Visual Studio 就「不是」必要項目。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段需要 [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]。 如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，就需要使用 .NET Framework 3.0。  
  
##  <a name="BKMK_SQL"></a> 安裝 SQL Server  
 安裝 [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)  
  
 安裝 [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)  
  
 安裝 [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)  
  
 當您安裝 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 時，請選取下列功能：  
  
-   Database Engine Services  
  
    -   SQL Server 複寫  
  
    -   全文檢索搜尋  
  
-   Analysis Services  
  
-   Reporting Services  
  
-   共用功能  
  
    -   SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) 或 Business Intelligence Development Studio (SQL Server 2008 R2)  
  
         [下載 SQL Server 2014 Data Tools](http://www.microsoft.com/download/details.aspx?id=42313)  
  
    -   用戶端工具連接性  
  
    -   Integration Services  
  
    -   管理工具 - 基本  
  
        -   管理工具 - 完整  
  
 **其他**  
  
-   除了二進位定序之外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援所有區分大小寫及不區分大小寫的 SQL Server 定序。 不支援二進位定序。  
  
-   為了達到最佳效能，Microsoft 建議使用 SQL Server Enterprise Edition。 請參閱 [SQL Server 2008 R2 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx)、[SQL Server 2012 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx)或 [SQL Server 2014 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx)。  
  
-   系統支援 Service Pack 和 Windows Update，因此皆應安裝。  
  
-   當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 位於不同的電腦時，分散式交易協調器 (MSDTC) 會處理電腦間的交易。 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能不支援 MSDTC 交易。 不支援 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能。  
  
##  <a name="BKMK_MQSeries"></a> 安裝 MQSeries 必要條件  
 **MQSeries 配接器**：在安裝 BizTalk Server 時即會自動安裝。  
  
 **MQSeries 用戶端 (MQSC) 配接器**：  
  
1.  執行 Host Integration Server (HIS) 安裝  
  
2.  在元件安裝中，展開 [BizTalk 配接器]。  
  
3.  選取 [BizTalk Adapter for WebSphere MQ (Client-Based) (適用於 WebSphere MQ (以用戶端為基礎) 的 BizTalk 配接器)]。  
  
 **支援的 IBM WebSphere MQ 版本**：  
  
-   IBM WebSphere MQ 6.0.2.12 及更新版  
  
-   IBM WebSphere MQ 7.0.1.9 及更新版  
  
-   IBM WebSphere MQ 7.1.0.5 及更新版  
  
-   IBM WebSphere MQ 7.5.0.3 及更新版  
  
-   IBM WebSphere MQ 8 (僅限執行階段；而非系統管理 API)  
  
     [Host Integration Server CU3](https://support.microsoft.com/kb/3019572) 中包含針對 MQ 第 8 版的支援。  
  
> [!NOTE]
>  如果未列出特定的 WebSphere MQ 版本 (例如 MQ 5.x)，表示這個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本並不支援。  
  
 **其他**  
  
-   最佳做法是一律安裝最新的 WebSphere MQ Fix Pack。 請參閱 [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037)。  
  
-   如果 IBM WebSphere MQ 是安裝在非 Windows 電腦上，請將 **MQSAgent COM+ 應用程式** (MQSConfigWiz.exe) 和 **MQSeries Server for Windows** 安裝在同一部電腦上。 如果 IBM WebSphere MQ 是安裝在 Windows 電腦上，則不需使用 **MQSAgent COM+ 應用程式**和 **MQSeries Server for Windows** 程式。  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝檔案包含 **MQSConfigWiz.exe**。  
  
     **MQSeries Server for Windows** 不是 Microsoft 程式，而必須透過 IBM WebSphere MQ 程式取得。  
  
-   [MQSeries 配接器](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx)提供 MQSeries 配接器的詳細資訊，包括不同元件的設定。 [BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) (BizTalk Server：MQSeries 和 MQSeries 用戶端 (MQSC) 配接器) 提供 MQSeries 和 MQSC 配接器的其他詳細資料。  
  
-   IBM WebSphere 並非 Microsoft 產品，因此 Microsoft 不提供支援服務。 Microsoft 亦不保證此程式的適用性。 如需 IBM WebSphere MQ 的詳細資訊，包括下載指示，請參閱 www.ibm.com。  
  
##  <a name="BKMK_BAMAlerts"></a> BAM 警示  
 [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] 或 [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 的 BAM 警示會使用 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Database Mail。 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 的 BAM 警示會使用 SQL Notification Services。 安裝或設定 BAM 警示之前，您必須先在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中設定 Notification Services 或 Database Mail。  
  
###  <a name="BKMK_DBMail"></a> 使用 SQL Server 2012/2014 的 BAM 警示  
 設定 [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx)。  
  
 設定 [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx)。  
  
 **其他**  
  
-   Database Mail 會使用 SMTP 伺服器來傳送 BAM 警示。 您可以將 SMTP 伺服器本機安裝在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或另一部 IIS 伺服器上。 [附錄 D：建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)中有提列安裝及設定 SMTP 伺服器的步驟。  
  
###  <a name="BKMK_SSNS"></a> 使用 SQL Server 2008 R2 的 BAM 警示 – 安裝 SQL Server 2005 Notification Services  
  
1.  請前往 [Microsoft SQL Server 2005 SP4 功能套件](http://go.microsoft.com/fwlink/p/?LinkId=286285)。  
  
2.  針對下列元件，下載並安裝適當的平台套件：  
  
     **Microsoft SQL Server Native Client**  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" X86 套件 (sqlncli.msi)  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" X64 套件 (sqlncli_x64.msi)  
  
     **Microsoft SQL Server 2005 管理物件集合**  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" X86 套件 (SQLServer2005_XMO.msi)  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" X64 套件 (SQLServer2005_XMO_x64.msi)  
  
     **Microsoft SQL Server 2005 Notification Services 用戶端元件**  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" X86 套件 (SQLServer2005_NS.msi)  
  
    -   HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" X64 套件 (SQLServer2005_NS_x64.msi)  
  
 **其他**  
  
-   您不需要設定 SQL Notification Services；只要將其安裝在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中即可。  
  
##  <a name="BKMK_WIF"></a> Windows Identity Foundation  
  
|||  
|-|-|  
|[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 8.1、[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 和 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2|Windows Identity Foundation 是隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。|  
|[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] SP1|您可前往 [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "http://www.microsoft.com/download/details.aspx?id=17331" 進行下載。|  
  
 **其他**  
  
-   [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器或 SharePoint Online 在與 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM) 搭配使用時需要 Windows Identity Foundation (WIF)。 具體來說：  
  
    |安裝選項|WIF 為必要項目|  
    |-------------------------|------------------|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器 (含 CSOM)|是|  
    |SharePoint Online (含 CSOM)|是|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器 Web 服務 (已被取代)|否|  
    |沒有 SharePoint|否|  
  
-   [附錄 B︰安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供有關 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 安裝選項的特定資訊。  
  
##  <a name="BKMK_WSS"></a> 安裝及設定 Microsoft SharePoint  
 安裝 [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)  
  
 安裝 [SharePoint Online 服務](http://technet.microsoft.com/library/jj819267.aspx)  
  
 安裝 [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)  
  
 安裝 [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)  
  
 **其他**  
  
-   如果您要安裝 SharePoint，就必須先安裝好 SharePoint，再繼續進行其餘 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必要條件。  
  
-   安裝和設定 SharePoint 包含下列程序：  
  
    -   安裝 SharePoint  
  
    -   設定 SharePoint  
  
    -   將預設的網站擴充成虛擬伺服器  
  
-   [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 BizTalk Server 適用的 SharePoint 配接器安裝選項。  
  
-   使用 SharePoint 配接器時，建議您安裝新的 CSOM 選項，而不是 SharePoint Web 服務 (如[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)所述)。  
  
##  <a name="BKMK_SharedMem"></a> 停用共用記憶體通訊協定  
  
1.  開啟 [SQL Server 組態管理員]。  
  
2.  在 [SQL Server 組態管理員] 中，依序展開 [SQL Server 網路組態] 和 [Protocols for MSSQLSERVER (MSSQLSERVER 的通訊協定)]。  
  
3.  以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。  
  
4.  選取 [SQL Server 服務]，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [停止]。 服務停止之後，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [啟動]。  
  
5.  關閉 [SQL Server 組態管理員]。  
  
 **其他**  
  
-   在特定負荷條件下 (例如用戶端從相同的電腦存取 SQL Server)，SQL Server 共用記憶體通訊協定可能會降低 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的效能。 您可以停用 [SQL Server 網路組態] 中的 [共用記憶體網路通訊協定] 來解決這個問題。  
  
-   ReplaceThisText  
  
##  <a name="BKMK_LocalAdmin"></a> 加入本機系統管理員群組  
 **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：[Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx) (Windows Server 2012：如何將帳戶新增至本機系統管理員群組)  
  
 **Windows 8.1**：若要開啟 Windows 8 的 [本機使用者和群組]，請按一下鍵盤上的 Windows 鍵，並輸入**群組**。 在 [搜尋] 視窗中，按一下 [設定]。 在 [結果] 視窗中，按一下 [編輯本機使用者和群組]。 按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。  
  
 **Windows 7 SP1**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入**電腦管理**，並按一下以開啟該項目。 展開 [本機使用者和群組]，按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。  
  
 **其他**  
  
-   您必須是本機系統管理員群組的成員才能安裝和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
##  <a name="BKMK_AppLog"></a> 設定應用程式事件記錄檔  
  
1.  開啟 [事件檢視器]：  
  
     **[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。 在 [結果] 視窗中，按一下 [事件檢視器]。  
  
     **Windows 8.1**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。 在 [搜尋] 視窗中，按一下 [設定]。 在 [結果] 視窗中，按一下 [檢視事件記錄檔]。  
  
     **Windows 7 SP1**：按一下 [開始]。 在 [搜尋] 文字方塊中，輸入**事件檢視器**，並按一下以開啟該項目。  
  
2.  展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後按一下 [屬性]。 在 [記錄內容] 中：  
  
    -   若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。  
  
    -   若要提供更多空間，請輸入 [最大記錄檔大小] 中較高的數字。  
  
    -   若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。  
  
    -   若要清除記錄檔事件，請選取 [清除記錄檔]。  
  
3.  按一下 [確定]，關閉 [事件檢視器]。  
  
 **其他**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式會將事件的記錄存放在應用程式事件記錄檔中。 應用程式記錄檔所需的空間量會根據安裝期間所安裝的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能而不同。 如果應用程式事件記錄檔在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝期間用盡空間，安裝就會失敗。 若要防止此錯誤，您可以變更應用程式事件記錄檔的設定。  
  
## <a name="next"></a>下一個  
 [選擇 BizTalk Server 功能和元件](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)   
 [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [附錄 C：可轉散發的封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [附錄 D︰建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
